---
title: Nicht-Regex-Umleitungen werden nach Fastly anstatt nach Nginx (Routen) abgeladen.
description: In diesem Thema wird eine Lösung für ein typisches Leistungsproblem vorgeschlagen, das auftreten könnte, wenn Sie Nicht-Regex-Umleitungen in der Cloud-Infrastruktur zu Fastly anstatt zu Nginx in Adobe Commerce abladen.
exl-id: 8b22d25d-0865-4d21-b275-d344ba8748f2
feature: Routes
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---

# Nicht-Regex-Umleitungen werden nach Fastly anstatt nach Nginx (Routen) abgeladen.

In diesem Thema wird eine Lösung für ein typisches Leistungsproblem vorgeschlagen, das auftreten könnte, wenn Sie Nicht-Regex-Umleitungen in der Cloud-Infrastruktur zu Fastly anstatt zu Nginx in Adobe Commerce abladen.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur (alle Versionen) `Master/Production/Staging` Umgebungen nutzen

## Problem

In Adobe Commerce in der Cloud-Infrastruktur kann eine große Anzahl von Nicht-Regex-Weiterleitungen/Rewrites nicht auf der Nginx-Ebene durchgeführt werden und kann daher Leistungsprobleme verursachen.

## Ursache

Die `routes.yaml` in der Datei `.magento/routes.yaml` definiert Routen für Ihre Adobe Commerce in der Cloud-Infrastruktur.

Wenn die Größe Ihrer `routes.yaml` -Datei 32 KB oder größer ist, sollten Sie Ihre Nicht-Regex-Umleitungen/Umschreibungen zu Fastly abladen.

Diese Nginx-Ebene kann nicht viele Nicht-Regex-Umleitungen/Umschreibungen verarbeiten, da sonst Leistungsprobleme auftreten.

## Lösung

Die Lösung besteht darin, diese Nicht-Regex-Umleitungen stattdessen auf Fastly zu laden. Erstellen Sie einen allgemeinen Fehlerpfad, um zu Fastly umzuleiten.

In den folgenden Schritten wird beschrieben, wie Sie Umleitungen auf Fastly statt auf Nginx platzieren.

1. Erstellen Sie ein Edge-Wörterbuch.

   Sie können zunächst [VCL-Snippets in Adobe Commerce](/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html) , um ein Kantenwörterbuch zu definieren. Diese enthält die Umleitungen.

   Einige Vorbehalte hierzu:

   * Fastly kann Regex bei Wörterbucheinträgen nicht ausführen. Es ist nur eine genaue Übereinstimmung. Weitere Informationen zu diesen Einschränkungen finden Sie unter [Fastly-Dokumente zu Einschränkungen bei Edge-Wörterbüchern](https://docs.fastly.com/guides/edge-dictionaries/about-edge-dictionaries#limitations-and-considerations).
   * Fastly hat eine Grenze von 1000 Einträgen in einem Wörterbuch. Fastly kann diese Grenze erweitern, aber das führt zum dritten Höhepunkt.
   * Jedes Mal, wenn Sie die Einträge aktualisieren und diese aktualisierte VCL auf allen Knoten bereitstellen, wird die geometrische Ladezeit mit erweiterten Wörterbüchern verlängert. Das bedeutet, dass ein 2000-Einträge-Wörterbuch tatsächlich 3 x 4 x 4 x langsamer lädt als ein 1000-Einträge-Wörterbuch. Dies ist jedoch nur ein Problem bei der Bereitstellung des VCL (Aktualisierung des Wörterbuchs oder Änderung des VCL-Funktionscodes).

     Dies hat keine Auswirkungen auf die Zeit, die die Verarbeitung einer Anfrage schnell dauert. Es hat nur Auswirkungen darauf, wie lange es schnell dauert, eine neue Konfiguration auszuführen.

     Im Allgemeinen dauern Konfigurationsänderungen im Durchschnitt einige Sekunden, in der Regel nicht mehr als 5-10 Sekunden. Eine 2fache Erhöhung der Wörterbucheinträge dauert also 30 Sekunden, bis Ihre Konfiguration eingeführt wird. Eine 4fache Erhöhung würde näher an 2 Minuten dauern. Dies führt zum vierten Vorbehalt.

   * Es gibt eine ziemlich harte Grenze von 10.000 Einträgen in einem Edge-Wörterbuch.

   Es wird dringend empfohlen, Ihre Umleitungsliste zu konsolidieren. Sie können mehrere Wörterbücher verwenden, aber beachten Sie bitte, dass jede Aktualisierung, die Sie an Ihrem VCL vornehmen, mehrere Minuten in Anspruch nehmen wird, um in Fastly zu füllen.

1. Vergleichen Sie die URL mit den Wörterbüchern.

   Wenn die URL-Suche erfolgt, wird der Vergleich durchgeführt, um den benutzerspezifischen Fehlercode anzuwenden, wenn eine Übereinstimmung gefunden wird.

   Verwenden Sie ein anderes VCL-Snippet, um so etwas wie Folgendes hinzuzufügen: `vcl_recv`:

   ```
        declare local var.redir-path STRING;
        set var.redir-path = table.lookup(redirects, std.tolower(req.url), "");
   
        if (var.redir-path != "") {
          error 912 var.redir-path;
        }
   ```

   Hier überprüfen wir, ob die URL im Tabelleneintrag vorhanden ist. Wenn dies der Fall ist, rufen wir einen internen Fastly-Fehler auf und übergeben die Umleitungs-URL aus der Tabelle an diesen Fehler.

1. Verwalten Sie die Umleitung.

   Wenn eine Übereinstimmung gefunden wird, wird die Aktion ausgeführt, die dafür definiert ist `obj.status`, in diesem Fall eine 301 dauerhafte Umleitung.

   Verwenden Sie einen endgültigen Ausschnitt in `vcl_error` , um die 301-Fehler-Codes zurück an den Client zu senden:

   ```
     if (obj.status == 912) {
        set obj.http.location = obj.response;
        set obj.status = 301;
        set obj.response = "Moved Permanently";
        return(deliver);
          }
   ```

   Mit diesem Block überprüfen wir, ob der Fehlercode von `vcl_recv` stimmt überein, und wenn ja, setzen wir den Speicherort auf die übergebene Fehlermeldung, ändern dann den Statuscode auf 301 und die Nachricht auf &quot;Dauerhaft verschoben&quot;. Zu diesem Zeitpunkt sollte die Antwort bereit sein, zum Client zurückzukehren.

### Staging-Service

>[!WARNING]
>
>Wenn Sie all diese Schritte ausprobieren möchten, wird dringend empfohlen, eine Adobe Commerce-Staging-Umgebung einzurichten. Auf diese Weise können Sie Tests für den Fastly-Dienst durchführen, um sicherzustellen, dass sich alles wie erwartet verhält.

Wenn Sie keine Adobe Commerce-Staging-Umgebung ausführen möchten, aber sehen möchten, wie diese Umleitungen aussehen würden, können Sie direkt in Fastly ein Staging-Konto einrichten.

## Verwandtes Lesen

* [Fastly VCL-Referenz](https://docs.fastly.com/vcl/)
* [Routen konfigurieren](/docs/commerce-cloud-service/user-guide/configure/routes/routes-yaml.html) in unserer Entwicklerdokumentation.
* [Schnelles Einrichten](/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) in unserer Entwicklerdokumentation.
* [VCL-Datenblatt für reguläre Ausdrücke](https://docs.fastly.com/en/guides/vcl-regular-expression-cheat-sheet) in unserer Entwicklerdokumentation.
