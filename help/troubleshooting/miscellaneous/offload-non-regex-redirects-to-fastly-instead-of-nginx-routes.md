---
title: Umleitungen von nicht-[!DNL regex] werden zu [!DNL Fastly] anstelle von [!DNL Nginx] (Routen) abgeladen.
description: In diesem Thema wird eine Lösung für ein typisches Leistungsproblem vorgeschlagen, das auftreten könnte, wenn Sie Umleitungen von Nicht-[!DNL regex] in der Cloud-Infrastruktur zu [!DNL Fastly] anstelle von [!DNL Nginx] in Adobe Commerce abladen.
exl-id: 8b22d25d-0865-4d21-b275-d344ba8748f2
feature: Routes
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 0%

---

# Umleitung von Nicht-[!DNL regex] auf [!DNL Fastly] anstelle von [!DNL Nginx] (Routen) abladen

In diesem Thema wird eine Lösung für ein typisches Leistungsproblem vorgeschlagen, das bei der Abladung von Nicht-[!DNL regex]-Umleitungen in der Cloud-Infrastruktur zu [!DNL Fastly] anstelle von [!DNL Nginx] in Adobe Commerce auftreten könnte.

## Betroffene Produkte und Versionen

* Adobe Commerce in Cloud-Infrastruktur (alle Versionen) `Master/Production/Staging`-Umgebungen mit [!DNL Fastly]

## Problem

In Adobe Commerce in der Cloud-Infrastruktur kann eine große Anzahl von Nicht-[!DNL regex]-Umleitungen/Umschreibungen nicht auf der [!DNL Nginx]-Ebene durchgeführt werden und kann daher Leistungsprobleme verursachen.

## Ursache

Die Datei &quot;`routes.yaml`&quot; im Ordner &quot;`.magento/routes.yaml`&quot; definiert Routen für Ihre Adobe Commerce in der Cloud-Infrastruktur.

Wenn die Größe Ihrer `routes.yaml`-Datei 32 KB oder größer ist, sollten Sie Ihre Nicht-[!DNL regex]-Umleitungen/Umschreibungen auf [!DNL Fastly] abladen.

Diese [!DNL Nginx]-Ebene kann nicht viele Nicht-[!DNL regex]-Umleitungen/Umschreibungen verarbeiten, da sonst Leistungsprobleme auftreten.

## Lösung

Die Lösung besteht darin, diese Umleitungen, die nicht-[!DNL regex] sind, stattdessen auf [!DNL Fastly] zu laden. Erstellen Sie einen allgemeinen Fehlerpfad, um zu [!DNL Fastly] umzuleiten.

In den folgenden Schritten wird beschrieben, wie Sie Umleitungen auf [!DNL Fastly] statt auf [!DNL Nginx] platzieren.

1. Erstellen Sie ein Edge-Wörterbuch.

   Zunächst können Sie [[!DNL VCL] Snippets in Adobe Commerce](/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html) verwenden, um ein Kantenwörterbuch zu definieren. Diese enthält die Umleitungen.

   Einige Vorbehalte hierzu:

   * [!DNL Fastly] kann für Wörterbucheinträge nicht [!DNL regex] tun. Es ist nur eine genaue Übereinstimmung. Weitere Informationen zu diesen Einschränkungen finden Sie in den Dokumenten von [[!DNL Fastly] zu den Einschränkungen für Edge-Wörterbücher](https://docs.fastly.com/guides/edge-dictionaries/about-edge-dictionaries#limitations-and-considerations).
   * [!DNL Fastly] erlaubt maximal 1000 Einträge in einem Wörterbuch. [!DNL Fastly] kann diese Grenze erweitern, was jedoch zum dritten Vorbehalt führt.
   * Jedes Mal, wenn Sie die Einträge aktualisieren und diese aktualisierte [!DNL VCL] für alle Knoten bereitstellen, wird die geometrische Ladezeit mit erweiterten Wörterbüchern verlängert. Das bedeutet, dass ein 2000-Einträge-Wörterbuch tatsächlich 3 x 4 mal langsamer lädt als ein 1000-Einträge-Wörterbuch. Dies ist jedoch nur ein Problem bei der Bereitstellung von [!DNL VCL] (Aktualisierung des Wörterbuchs oder Änderung des Funktionscodes [!DNL VCL]).

     Die Verarbeitung einer Anforderung hat keine Auswirkungen auf die Zeit, die [!DNL Fastly] in Anspruch nimmt. Sie hat lediglich Auswirkungen darauf, wie lange [!DNL Fastly] dauert, bis eine neue Konfiguration veröffentlicht wird.

     Im Allgemeinen dauern Konfigurationsänderungen im Durchschnitt einige Sekunden, in der Regel nicht mehr als 5-10 Sekunden. Eine 2fache Erhöhung der Wörterbucheinträge dauert also 30 Sekunden, bis Ihre Konfiguration eingeführt wird. Eine 4fache Erhöhung würde näher an 2 Minuten dauern. Dies führt zum vierten Vorbehalt.

   * Es gibt eine ziemlich harte Grenze von 10.000 Einträgen in einem Edge-Wörterbuch.

   Es wird dringend empfohlen, Ihre Umleitungsliste zu konsolidieren. Sie können mehrere Wörterbücher verwenden. Beachten Sie jedoch, dass es mehrere Minuten dauern wird, bis alle Aktualisierungen, die Sie an Ihrem [!DNL VCL] vornehmen, tatsächlich über [!DNL Fastly] aufgefüllt sind.

1. Vergleichen Sie die [!DNL URL] mit den Wörterbüchern.

   Wenn die [!DNL URL] -Suche auftritt, wird der Vergleich durchgeführt, um den benutzerspezifischen Fehlercode anzuwenden, wenn eine Übereinstimmung gefunden wird.

   Verwenden Sie ein weiteres [!DNL VCL]-Snippet, um `vcl_recv` etwas wie Folgendes hinzuzufügen:

   ```
        declare local var.redir-path STRING;
        set var.redir-path = table.lookup(redirects, std.tolower(req.url), "");
   
        if (var.redir-path != "") {
          error 912 var.redir-path;
        }
   ```

   In unserem Beispiel überprüfen wir, ob die [!DNL URL] im Tabelleneintrag vorhanden ist. Wenn dies der Fall ist, rufen wir einen internen [!DNL Fastly]-Fehler auf und übergeben an diesen Fehler die Umleitung [!DNL URL] von der Tabelle.

1. Verwalten Sie die Umleitung.

   Wenn eine Übereinstimmung gefunden wird, wird die Aktion ausgeführt, die für diesen `obj.status` definiert ist, in diesem Fall eine 301 dauerhafte Umleitung zum Verschieben.

   Verwenden Sie einen endgültigen Ausschnitt in `vcl_error`, um die 301-Fehlercodes zurück an den Client zu senden:

   ```
     if (obj.status == 912) {
        set obj.http.location = obj.response;
        set obj.status = 301;
        set obj.response = "Moved Permanently";
        return(deliver);
          }
   ```

   Mit diesem Block überprüfen wir, ob der von `vcl_recv` übergebene Fehlercode übereinstimmt. Wenn ja, setzen wir den Speicherort auf die übergebene Fehlermeldung, ändern dann den Statuscode auf 301 und die Nachricht auf &quot;Dauerhaft verschoben&quot;. Zu diesem Zeitpunkt sollte die Antwort bereit sein, zum Client zurückzukehren.

### Staging-Service

>[!WARNING]
>
>Wenn Sie all diese Schritte ausprobieren möchten, wird dringend empfohlen, eine Adobe Commerce-Staging-Umgebung einzurichten. Auf diese Weise können Sie Tests für den Dienst [!DNL Fastly] ausführen, um sicherzustellen, dass sich alles wie erwartet verhält.

Wenn Sie keine Adobe Commerce-Staging-Umgebung ausführen möchten, aber sehen möchten, wie diese Umleitungen aussehen würden, können Sie ein Staging-Konto direkt auf [!DNL Fastly] einrichten.

## Verwandtes Lesen

* [[!DNL Fastly VCL] reference](https://docs.fastly.com/vcl/)
* [Konfigurieren von Routen](/docs/commerce-cloud-service/user-guide/configure/routes/routes-yaml.html) in unserer Entwicklerdokumentation
* [ Richten Sie  [!DNL Fastly]](/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) in unserer Entwicklerdokumentation ein.
* [[!DNL VCL] Datenblatt zum regulären Ausdruck](https://docs.fastly.com/en/guides/vcl-regular-expression-cheat-sheet) in unserer Entwicklerdokumentation
* [Best Practices für die Änderung von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Playbook für die Commerce-Implementierung
