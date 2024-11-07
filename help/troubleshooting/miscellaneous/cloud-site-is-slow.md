---
title: Cloud-Site ist langsam
description: Dieser Artikel enthält Empfehlungen dazu, wie Sie Ihre Adobe Commerce auf der Cloud-Infrastruktur-Site bei hoher Traffic-Last leistungsfähiger machen und wie Sie diese Last reduzieren können.
exl-id: 144df36b-6305-4e57-b813-46bbb0ddedda
feature: Cache, Categories, Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '1064'
ht-degree: 0%

---

# Cloud-Site ist langsam

Dieser Artikel enthält Empfehlungen dazu, wie Sie Ihre Adobe Commerce auf der Cloud-Infrastruktur-Site bei hoher Traffic-Last leistungsfähiger machen und wie Sie diese Last reduzieren können.

## Betroffene Versionen und Editionen

* Adobe Commerce in der Cloud-Infrastruktur, alle Versionen

## Problem

<u>Zu reproduzierende Schritte</u>

1. Besuchen Sie Ihren Adobe Commerce Store.
1. Navigieren Sie zu einer Kategorieseite.
1. Fügen Sie dem Warenkorb ein Produkt hinzu.

<u>Erwartetes Ergebnis</u>

Die Website ist responsiv und das Hinzufügen eines Produkts zum Warenkorb erfolgt schnell.

<u>Tatsächliches Ergebnis</u>

Die Site ist langsam, oder die Kategorieseiten sind schnell, aber die Warenkorbseite ist langsam.

## Debugging von Schritten und Lösungen

Führen Sie die folgenden Schritte aus, um den Grund der langsamen Leistung zu verfolgen und zu beheben. Sie können den ersten und zweiten Schritt wechseln, aber nur dann mit dem Blockieren von IPs fortfahren, wenn die Optimierung der Cacheeinstellungen nicht hilft.

1. Überprüfen Sie die Cache-Trefferrate für Seiten mit hohem Traffic und reduzieren Sie die Menge der stark aktualisierten Daten.
1. Überprüfen Sie die Gesamtanzahl der Treffer im Site-Cache und überprüfen Sie die allgemeine Cache-/Fastly-Konfiguration.
1. Identifizieren Sie die Web-Clients, die die hohe Server-Last verursachen, und blockieren Sie IPs, die die hohe Belastung verursachen.

Die folgenden Absätze enthalten weitere Details zu jedem Schritt.

### Schritt 1: Überprüfen der Cache-Trefferrate für die Seiten mit hohem Traffic

Der erste Schritt zur Behebung einer Site, die durch starken Traffic unterdrückt wurde, besteht darin, sicherzustellen, dass die Seiten mit dem höchsten Traffic, wie die Homepage des Stores und die Kategorieseiten der obersten Ebene, ordnungsgemäß zwischengespeichert werden.

Sie können die Cache-Trefferraten für diese Seiten ermitteln, indem Sie die `X-Cache` HTTP-Header mit cURL überprüfen, wie in der Schnelldokumentation unter [Überprüfen des Caches mit cURL](https://docs.fastly.com/guides/debugging/checking-cache#using-curl) beschrieben. Oder überprüfen Sie dieselben Header über die Registerkarte &quot;Netzwerk&quot;in der Entwickler-Symbolleiste Ihres bevorzugten Webbrowsers.

Die von der Anwendung stammenden Antwortheader werden im Allgemeinen weitestgehend berücksichtigt. Wenn die Header jedoch alle auf &quot;Nicht zwischenspeichern&quot;festgelegt sind und die Seite &quot;in der Vergangenheit ablaufen&quot;soll, kann die Seite schnell nicht zwischengespeichert werden.

>[!WARNING]
>
>Beachten Sie, dass sich Antwortheader schnell ändern. Wenn Sie also die Haupt-URL mit cURL oder dem Webbrowser überprüfen, wird nicht unbedingt angezeigt, welche Header von der Anwendung ausgegeben werden. Häufig antwortet Fastly selbst auf Webbrowser mit Headern &quot;ohne Cache&quot;, aber die Webanwendung selbst gestattet die Zwischenspeicherung, und das Element wird von Fastly ordnungsgemäß zwischengespeichert. Die Informationen zu den Headern &quot;cache-control&quot;und &quot;pragma&quot;sind in diesem Fall also nicht nützlich.

#### Fehlerbehebung für Seiten mit hohem Traffic

Wenn die Indexseite eine niedrige Trefferrate aufweist, können Sie sie beheben, indem Sie die Menge der stark aktualisierten Daten auf dieser Seite reduzieren.

### Schritt 2: Überprüfen der gesamten Site-Cache-Trefferrate

Überprüfen der gesamten Cache-Trefferrate:

1. [Schnelle Anmeldeinformationen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration) für Ihre Adobe Commerce in der Cloud-Infrastrukturumgebung abrufen.
1. Führen Sie den folgenden cURL-Befehl für Linux/macOS aus, um die Trefferrate für Ihre Site in den letzten 30 Minuten zu überprüfen, wobei Sie die Werte für Ihre Fastly-Anmeldedaten ersetzen:

   `curl -H "Fastly-Key: " https://api.fastly.com/stats/service//field/hit_ratio?by=minute | json_pp`

   Sie können auch die historischen Trefferraten über den letzten Tag oder Monat überprüfen, indem Sie die Abfrageoption für den Zeitraum von `?by=minute` in `?by=hour` oder `?by=day` ändern. Weitere Informationen zum Abrufen von Fastly-Cache-Statistiken finden Sie unter [Abfrageoptionen](https://docs.fastly.com/api/stats#Query) in der Schnelldokumentation.

   Die Option `| json_pp` druckt die JSON-Antwortausgabe mit dem Dienstprogramm `json_pp` ziemlich. Wenn Sie den Fehler &quot;_&#39;json\_pp nicht gefunden&quot;_ erhalten, installieren Sie das Dienstprogramm &quot;`json_pp`&quot;oder verwenden Sie ein anderes Befehlszeilenwerkzeug für JSON-Drucken, das schön ist. Alternativ können Sie den Parameter `| json_pp` löschen und den Befehl erneut ausführen. Die JSON-Antwortausgabe ist nicht formatiert, aber Sie können sie über eine JSON-Verschönerung ausführen, um sie zu bereinigen.

Eine Trefferrate über 0,90 oder 90 % zeigt an, dass der vollständige Seiten-Cache funktioniert.

Eine Trefferrate unter 0,85 oder 85 % kann auf ein Site-Konfigurationsproblem hinweisen oder Sie haben möglicherweise eine Drittanbieter-Erweiterung installiert, die nicht zulässt, dass der Inhalt zwischengespeichert wird.

#### Fehlerbehebung für die gesamte Cache-Trefferrate

1. Bestimmen Sie mithilfe der Statistiken zur stündlichen und täglichen Trefferrate, wann die Trefferrate zu sinken begann. Wenn die Trefferrate plötzlich um den Zeitpunkt abstürzte, zu dem Sie eine Änderung auf Ihrer Site vorgenommen haben, sollten Sie erwägen, die Änderung so lange zurückzufahren, bis die Site-Last heruntergefahren ist.
1. Überprüfen Sie die Konfiguration in Commerce Admin unter **Stores** > **Konfiguration** > Erweitert > **System** > **Gesamter Seiten-Cache**. Stellen Sie sicher, dass der Wert **TTL für den öffentlichen Inhalt** nicht zu niedrig eingestellt ist.
1. Vergewissern Sie sich, dass Sie [die VCL-Snippets hochgeladen haben](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#upload-vcl-snippets).
1. Wenn Sie benutzerdefinierte VCL-Snippets verwenden, debuggen Sie sie zur korrekten Verwendung der Aktionen &quot;pass&quot;oder &quot;pipe&quot;: Sie sollten sorgfältig und zumindest mit einer bestimmten Bedingung verwendet werden. Weitere Tipps finden Sie unter [Benutzerdefinierte Fastly VCL-Snippets](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets) in unserer Entwicklerdokumentation.

### Schritt 3: Identifizieren Sie die Websites, die die hohe Server-Last verursachen.

Sie können eine der folgenden Methoden verwenden, um Informationen zu den IP-Adressen zu erhalten, die auf Ihren Adobe Commerce Store zugreifen.

* Überprüfen Sie die HTTP-Zugriffsprotokolle über eine SSH-Sitzung.
* Wenden Sie sich an den Adobe Commerce-Support, um eine Liste von IP-Adressen anzufordern, die eine hohe Belastung der Site verursachen.

#### Überprüfen der HTTP-Zugriffsprotokolle

Um das Zugriffsprotokoll Ihrer Site anzuzeigen, führen Sie den folgenden Befehl in Ihrer lokalen Entwicklungsumgebung aus:

```bash
magento-cloud log access
```

Weitere Zeilen mit dem

```bash
--lines
```

-Option, beispielsweise:

```bash
magento-cloud log access --lines=500
```

Sie können dieses Protokoll anzeigen und überprüfen, ob ein großer Teil der Anfragen von einer bestimmten IP-Adresse stammt. Eine andere Möglichkeit besteht darin, `awk` , `sort` und `uniq` zu verwenden, um die am häufigsten auftretenden IP-Adressen im Protokoll automatisch zu zählen, z. B.:

```bash
magento-cloud log access --lines 2000 | awk '{print $1}' | sort | uniq -c | sort
  -nr
```

Wenn die Variable

```bash
magento-cloud log
```

nicht funktioniert, können Sie mit SSH eine Verbindung zum Remote-Server herstellen und die Protokolldatei unter `/var/log/access.log` überprüfen.

Nachdem Sie die IP-Adressen identifiziert haben, die eine hohe Serverlast verursachen, können Sie sie blockieren, indem Sie eine IP-Blockierungsliste aus dem Commerce Admin-Bedienfeld unter **Speicher** > **Konfiguration** > ERWEITERT > **System** > **Vollständiger Seiten-Cache** > **Fastly Configuration** > **Blockieren** konfigurieren konfigurieren konfigurieren.

Wenn Sie aufgrund hoher Auslastung nicht auf Ihren Admin zugreifen können, können Sie mit der Fastly-API die Blockierungsregeln einrichten:

1. Erstellen Sie die ACL wie im Dokument [Arbeiten mit ACLs mit der API](https://docs.fastly.com/guides/access-control-lists/working-with-acls-using-the-api) Fastly beschrieben.
1. Erstellen Sie im Abschnitt `recv` ein VCL-Snippet mit folgendem Inhalt, nachdem Sie ACL\_NAME\_GOES\_HERE durch den Namen der im vorherigen Schritt erstellten ACL ersetzt haben:

   ```
   if( req.http.Fastly-Client-IP ~ ACL_NAME_GOES_HERE ) {
   error 403 "Forbidden";
   }
   ```

Weitere Informationen zum Blockieren von IP-Adressen finden Sie im Handbuch zum [Fastly Adobe Commerce-Modul](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) in GitHub.
