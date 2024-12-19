---
title: Cloud-Site ist langsam
description: Dieser Artikel enthält Empfehlungen dazu, wie Sie die Leistung Ihrer Adobe Commerce auf einer Cloud-Infrastruktur-Site bei starkem Traffic verbessern und diese Last reduzieren können.
exl-id: 144df36b-6305-4e57-b813-46bbb0ddedda
feature: Cache, Categories, Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '1064'
ht-degree: 0%

---

# Cloud-Site ist langsam

Dieser Artikel enthält Empfehlungen dazu, wie Sie die Leistung Ihrer Adobe Commerce auf einer Cloud-Infrastruktur-Site bei starkem Traffic verbessern und diese Last reduzieren können.

## Betroffene Versionen

* Adobe Commerce auf Cloud-Infrastruktur, alle Versionen

## Problem

<u>Schritte zur Reproduktion</u>

1. Besuchen Sie Ihren Adobe Commerce-Store.
1. Durchsuchen einer Kategorieseite.
1. Fügen Sie ein Produkt zum Warenkorb hinzu.

<u>Erwartetes Ergebnis</u>

Die Site ist responsiv und das Hinzufügen eines Produkts zum Warenkorb ist schnell.

<u>Tatsächliches Ergebnis</u>

Die Site ist langsam oder die Kategorieseiten sind schnell, aber die Warenkorbseite ist langsam.

## Debugging-Schritte und -Lösungen

Führen Sie die folgenden Schritte aus, um den Grund für die langsame Leistung zu ermitteln und zu beheben. Sie können den ersten und den zweiten Schritt wechseln, aber mit dem Blockieren von IPs nur fortfahren, wenn die Optimierung der Cache-Einstellungen nicht hilft.

1. Überprüfen Sie die Cache-Trefferrate für Seiten mit hohem Traffic und reduzieren Sie die Menge stark aktualisierter Daten.
1. Überprüfen Sie die Gesamttrefferrate für den Site-Cache und überprüfen Sie die allgemeine Cache-/Fastly-Konfiguration.
1. Identifizieren Sie die Webclients, die die hohe Serverauslastung verursachen, und blockieren Sie die IPs, die die hohe Auslastung verursachen.

Die folgenden Absätze enthalten weitere Details für jeden Schritt.

### Schritt 1: Überprüfen Sie die Cache-Trefferrate für die Seiten mit hohem Traffic

Der erste Schritt zur Behebung einer durch hohen Traffic blockierten Site besteht darin, sicherzustellen, dass die Seiten mit dem höchsten Traffic, wie die Startseite des Stores und die Kategorieseiten der obersten Ebene, ordnungsgemäß zwischengespeichert werden.

Sie können die Cache-Trefferraten für diese Seiten ermitteln, indem Sie die `X-Cache` HTTP-Header mithilfe von cURL lesen, wie unter [Überprüfen des Cache mithilfe von cURL](https://docs.fastly.com/guides/debugging/checking-cache#using-curl) in der Fastly-Dokumentation beschrieben. Oder überprüfen Sie dieselben Header über die Registerkarte Netzwerk in der Entwickler-Symbolleiste Ihres bevorzugten Webbrowsers.

Fastly respektiert im Allgemeinen die Antwort-Header, die von der Anwendung kommen. Wenn die Header jedoch alle auf „nicht zwischenspeichern“ eingestellt sind und die Seite „in der Vergangenheit abläuft“, kann Fastly die Seite nicht zwischenspeichern.

>[!WARNING]
>
>Beachten Sie, dass Fastly die Antwort-Header ändert. Wenn Sie also die Haupt-URL mit cURL oder dem Webbrowser überprüfen, wird nicht unbedingt angezeigt, welche Header von der Anwendung ausgegeben werden. Es ist üblich, dass Fastly selbst auf Webbrowser ohne Cache-Header reagiert, aber die Webanwendung selbst ermöglicht das Caching und Fastly speichert das Element ordnungsgemäß zwischen. Die Header-Informationen „cache-control“ und „pragma“ sind in diesem Fall nicht nützlich.

#### Fehlerbehebung bei Seiten mit hohem Traffic

Wenn die Indexseite eine niedrige Trefferrate aufweist, können Sie sie beheben, indem Sie die Menge der auf dieser Seite vorhandenen stark aktualisierten Daten reduzieren.

### Schritt 2: Überprüfen Sie die Gesamttrefferrate für den Site-Cache

So überprüfen Sie die allgemeine Cache-Trefferrate:

1. [Abrufen von Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration)-Anmeldeinformationen für Ihre Adobe Commerce in der Cloud-Infrastrukturumgebung.
1. Führen Sie den folgenden Linux/macOS cURL-Befehl aus, um die Trefferrate für Ihre Site in den letzten 30 Minuten zu überprüfen, und ersetzen Sie und durch die Werte für Ihre Fastly-Anmeldeinformationen:

   `curl -H "Fastly-Key: " https://api.fastly.com/stats/service//field/hit_ratio?by=minute | json_pp`

   Sie können auch die historischen Trefferraten der letzten Tage oder Monate überprüfen, indem Sie die Abfrageoption „Zeitbereich“ von `?by=minute` in `?by=hour` oder `?by=day` ändern. Weitere Informationen zum Abrufen von Fastly-Cache-Statistiken finden Sie [Abfrageoptionen](https://docs.fastly.com/api/stats#Query) in der Fastly-Dokumentation.

   Mit der Option `| json_pp` wird die JSON-Antwortausgabe mit dem `json_pp`-Dienstprogramm quasi gedruckt. Wenn der Fehler „a_&#39;json\_pp not found&#39;_“ auftritt, installieren Sie das `json_pp`-Dienstprogramm oder verwenden Sie ein anderes Befehlszeilen-Tool für den JSON-Druck. Alternativ können Sie den `| json_pp` löschen und den Befehl erneut ausführen. Die JSON-Antwortausgabe ist nicht formatiert, Sie können sie jedoch über einen JSON-Verschönerer ausführen, um sie zu bereinigen.

Eine Trefferrate über 0,90 oder 90 % zeigt an, dass der Vollseiten-Cache funktioniert.

Eine Trefferrate unter 0,85 oder 85 % kann auf ein Site-Konfigurationsproblem hinweisen oder Sie haben möglicherweise eine Drittanbietererweiterung installiert, die den Inhalt nicht zwischenspeichert.

#### Fehlerbehebung für die allgemeine Cache-Trefferrate

1. Ermitteln Sie mithilfe der Statistiken zur stündlichen und täglichen Trefferrate, wann der Rückgang der Trefferrate begonnen hat. Wenn die Trefferrate etwa zur gleichen Zeit wie bei der Bereitstellung einer Site-Änderung plötzlich zurückging, sollten Sie in Erwägung ziehen, die Änderung rückgängig zu machen, bis die Site-Last sinkt.
1. Überprüfen Sie die Konfiguration im Commerce Admin unter **Stores** > **Configuration** > Erweitert > **System** > **Vollständiger Seitencache**. Stellen Sie sicher, dass **TTL für öffentliche Inhalte** nicht zu niedrig eingestellt ist.
1. Stellen Sie sicher, [ Sie die VCL-Snippets hochgeladen ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#upload-vcl-snippets).
1. Wenn Sie benutzerdefinierte VCL-Snippets verwenden, debuggen Sie diese für die korrekte Verwendung der „Pass“- oder „Pipe“-Aktionen: Sie sollten sorgfältig verwendet und zumindest mit einer bestimmten Bedingung verwendet werden. Weitere Tipps finden Sie unter [Benutzerdefinierte Fastly-VCL-Snippets](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets) in unserer Entwicklerdokumentation.

### Schritt 3: Identifizieren Sie die Websites, die die hohe Server-Last verursachen

Sie können eine der folgenden Methoden verwenden, um Informationen über die IP-Adressen abzurufen, die auf Ihren Adobe Commerce-Store zugreifen.

* Überprüfen Sie die HTTP-Zugriffsprotokolle über eine SSH-Sitzung.
* Wenden Sie sich an den Adobe Commerce-Support , um eine Liste der IP-Adressen anzufordern, die die Website stark belasten.

#### Überprüfen der HTTP-Zugriffsprotokolle

Um das Zugriffsprotokoll Ihrer Site anzuzeigen, führen Sie den folgenden Befehl in Ihrer lokalen Entwicklungsumgebung aus:

```bash
magento-cloud log access
```

Weitere Zeilen mit dem

```bash
--lines
```

Option, zum Beispiel:

```bash
magento-cloud log access --lines=500
```

Sie können dieses Protokoll anzeigen und überprüfen, ob ein großer Teil der Anfragen von einer bestimmten IP-Adresse stammt. Eine andere Möglichkeit besteht darin, `awk` , `sort` und `uniq` zu verwenden, um die im Protokoll am häufigsten vorkommenden IP-Adressen automatisch zu zählen, z. B.:

```bash
magento-cloud log access --lines 2000 | awk '{print $1}' | sort | uniq -c | sort
  -nr
```

Wenn die

```bash
magento-cloud log
```

-Befehl nicht funktioniert. Sie können mit SSH eine Verbindung zum Remote-Server herstellen und die Protokolldatei unter `/var/log/access.log` überprüfen.

Nachdem Sie die IP-Adressen identifiziert haben, die eine hohe Server-Belastung verursachen, können Sie sie blockieren, indem Sie eine IP-Blockierungsliste im Commerce Admin-Bedienfeld unter **Stores** > **Configuration** > ERWEITERT **System** > **Vollständiger Seitencache** > **Fastly Configuration** > **Blocking** konfigurieren.

Wenn Sie aufgrund hoher Auslastung nicht auf Ihren Administrator zugreifen können, können Sie die Sperrregeln mit der Fastly-API einrichten:

1. Erstellen Sie die ACL wie im Dokument [Arbeiten mit ACLs unter Verwendung der API](https://docs.fastly.com/guides/access-control-lists/working-with-acls-using-the-api) Fastly beschrieben.
1. Erstellen Sie im `recv` Abschnitt ein VCL-Snippet mit folgendem Inhalt, nachdem Sie ACL\_NAME\_GOES\_HERE durch den Namen der im vorherigen Schritt erstellten ACL ersetzt haben:

   ```
   if( req.http.Fastly-Client-IP ~ ACL_NAME_GOES_HERE ) {
   error 403 "Forbidden";
   }
   ```

Weitere Informationen zum Sperren von IP-Adressen finden Sie im [Fastly Adobe Commerce-Modulhandbuch](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) in GitHub.
