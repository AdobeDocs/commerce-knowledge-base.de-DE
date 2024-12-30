---
title: Nicht [!DNL regex] auslagern leitet zu/ [!DNL Fastly] anstelle [!DNL Nginx] (routes) um
description: In diesem Thema wird eine Lösung für ein typisches Leistungsproblem bei Umleitungen vorgeschlagen, das beim Abladen von Umleitungen von nicht [!DNL regex] in  [!DNL Fastly] /anstelle  [!DNL Nginx]  Adobe Commerce in der Cloud-Infrastruktur auftreten könnte.
exl-id: 8b22d25d-0865-4d21-b275-d344ba8748f2
feature: Routes
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 0%

---

# Nicht [!DNL regex] auslagern leitet zu [!DNL Fastly] anstatt zu [!DNL Nginx] um (Routen)

In diesem Abschnitt wird eine Lösung für ein typisches Leistungsproblem bei Weiterleitungen vorgeschlagen, das auftreten kann, wenn Sie in der Cloud-Infrastruktur nicht [!DNL regex] Weiterleitungen an [!DNL Fastly] anstatt [!DNL Nginx] in Adobe Commerce abladen.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur (alle Versionen) `Master/Production/Staging` Umgebungen, die [!DNL Fastly] nutzen

## Problem

In Adobe Commerce auf Cloud-Infrastrukturen können viele nicht [!DNL regex] Umleitungen/Umschreibungen nicht auf der [!DNL Nginx] vorgenommen werden, was zu Leistungsproblemen führen kann.

## Ursache

Die `routes.yaml`-Datei im `.magento/routes.yaml` definiert Routen für Ihre Adobe Commerce in der Cloud-Infrastruktur.

Wenn die Größe Ihrer `routes.yaml`-Datei 32 KB oder größer ist, sollten Sie Ihre nicht [!DNL regex] Umleitungen/Umschreibungen auf [!DNL Fastly] auslagern.

Diese [!DNL Nginx] kann eine große Anzahl nicht [!DNL regex] Umleitungen/Umschreibungen nicht verarbeiten, da sonst Leistungsprobleme auftreten.

## Lösung

Die Lösung besteht darin, diese nicht [!DNL regex] Weiterleitungen stattdessen nach [!DNL Fastly] abzuladen. Erstellen Sie einen generischen Fehlerpfad, um zu [!DNL Fastly] umzuleiten.

In den folgenden Schritten wird beschrieben, wie Sie Umleitungen auf [!DNL Fastly] anstatt auf [!DNL Nginx] platzieren.

1. Erstellen Sie ein Edge-Wörterbuch.

   Zunächst können Sie [[!DNL VCL] Snippets in Adobe Commerce) verwenden](/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html) um ein Edge-Wörterbuch zu definieren. Dies enthält die Umleitungen.

   Einige Vorbehalte:

   * [!DNL Fastly] können [!DNL regex] nicht auf Wörterbucheinträge anwenden. Es ist nur eine exakte Übereinstimmung. Weitere Informationen zu diesen Einschränkungen finden Sie in den Dokumenten zu Edge-Wörterbuchbeschränkungen von [[!DNL Fastly]](https://docs.fastly.com/guides/edge-dictionaries/about-edge-dictionaries#limitations-and-considerations).
   * [!DNL Fastly] ist auf 1.000 Einträge in einem einzelnen Wörterbuch beschränkt. [!DNL Fastly] können diese Grenze erweitern, aber das führt zum dritten Vorbehalt.
   * Jedes Mal, wenn Sie die Einträge aktualisieren und diese aktualisierten [!DNL VCL] auf allen Knoten bereitstellen, erhöht sich die geometrische Ladezeit mit sich erweiternden Wörterbüchern - was bedeutet, dass ein Wörterbuch mit 2000 Einträgen tatsächlich 3x-4x langsamer geladen wird als ein Wörterbuch mit 1000 Einträgen. Dies ist jedoch nur dann ein Problem, wenn Sie die [!DNL VCL] bereitstellen (das Wörterbuch aktualisieren oder den [!DNL VCL] ändern).

     Die Zeit, die für die Verarbeitung einer Anfrage [!DNL Fastly] ist, wird nicht beeinflusst. Sie wirkt sich nur darauf aus, wie lange es [!DNL Fastly], eine neue Konfiguration zu verarbeiten.

     Im Allgemeinen dauern Konfigurationsänderungen im Durchschnitt einige Sekunden, normalerweise nicht mehr als 5-10 Sekunden. Es dauert also mehr als 30 Sekunden, bis die Konfiguration zweimal so viele Wörterbuchelemente enthält. Eine 4-fache Erhöhung würde etwa 2 Minuten in Anspruch nehmen. Dies führt zum vierten Vorbehalt.

   * Es gibt eine ziemlich harte Grenze von 10.000 Einträgen in einem Edge-Wörterbuch.

   Es wird dringend empfohlen, Ihre Weiterleitungsliste zu konsolidieren. Sie können mehrere Wörterbücher verwenden. Beachten Sie jedoch, dass es bei jeder Aktualisierung Ihres [!DNL VCL] mehrere Minuten dauert, bis das Wörterbuch in allen [!DNL Fastly] aktualisiert ist.

1. Vergleichen Sie die [!DNL URL] mit den Wörterbüchern.

   Wenn die [!DNL URL] Suche stattfindet, wird der Vergleich durchgeführt, um den benutzerdefinierten Fehler-Code anzuwenden, falls eine Übereinstimmung gefunden wird.

   Verwenden Sie ein anderes [!DNL VCL], um `vcl_recv` etwas wie das Folgende hinzuzufügen:

   ```
        declare local var.redir-path STRING;
        set var.redir-path = table.lookup(redirects, std.tolower(req.url), "");
   
        if (var.redir-path != "") {
          error 912 var.redir-path;
        }
   ```

   Hier überprüfen wir, ob die [!DNL URL] im Tabelleneintrag vorhanden ist. Wenn dies der Fall ist, rufen wir einen internen [!DNL Fastly]-Fehler auf und übergeben an diesen Fehler die Umleitungs-[!DNL URL] aus der Tabelle.

1. Verwalten Sie die Umleitung.

   Wenn eine Übereinstimmung gefunden wird, wird die für diese `obj.status` definierte Aktion durchgeführt, in diesem Fall eine 301-dauerhafte Umleitung zur Verschiebung.

   Verwenden Sie einen endgültigen Ausschnitt in `vcl_error`, um die 301-Fehler-Codes zurück an den Client zu senden:

   ```
     if (obj.status == 912) {
        set obj.http.location = obj.response;
        set obj.status = 301;
        set obj.response = "Moved Permanently";
        return(deliver);
          }
   ```

   Mit diesem Block prüfen wir, ob der von `vcl_recv` übergebene Fehlercode übereinstimmt. Wenn ja, legen wir den Speicherort auf die übergebene Fehlermeldung fest und ändern dann den Status-Code in 301 und die Nachricht in „Dauerhaft verschoben“. An diesem Punkt sollte die Antwort bereit sein, zum Client zurückzukehren.

### Staging-Service

>[!WARNING]
>
>Wenn Sie alle diese Schritte ausprobieren möchten, wird dringend empfohlen, eine Adobe Commerce-Staging-Umgebung einzurichten. Auf diese Weise können Sie Tests mit dem [!DNL Fastly]-Service durchführen, um sicherzustellen, dass alles wie erwartet funktioniert.

Wenn Sie keine Adobe Commerce-Staging-Umgebung ausführen möchten, aber sehen möchten, wie diese Umleitungen aussehen würden, können Sie ein Staging-Konto direkt auf [!DNL Fastly] einrichten.

## Verwandtes Lesen

* [[!DNL Fastly VCL] Referenz](https://docs.fastly.com/vcl/)
* [Konfigurieren von Routen](/docs/commerce-cloud-service/user-guide/configure/routes/routes-yaml.html) in unserer Entwicklerdokumentation
* [Einrichten [!DNL Fastly]](/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) in unserer Entwicklerdokumentation
* [[!DNL VCL] Cheat Sheet für reguläre Ausdrücke](https://docs.fastly.com/en/guides/vcl-regular-expression-cheat-sheet) in unserer Entwicklerdokumentation
* [Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook
