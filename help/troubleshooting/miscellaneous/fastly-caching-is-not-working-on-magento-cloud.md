---
title: Die schnelle Zwischenspeicherung funktioniert in Adobe Commerce in der Cloud-Infrastruktur nicht
description: Dieser Artikel enthält eine Fehlerbehebung für das schnelle Zwischenspeichern, das auf Ihrer Site nicht funktioniert. Fastly ist ein CDN- und Caching-Dienst, der in Adobe Commerce in Cloud-Infrastrukturplänen und -Implementierungen enthalten ist. Um zu überprüfen, ob die Fastly-Erweiterung funktioniert, oder um die Fastly-Erweiterung zu debuggen, können Sie den curl-Befehl verwenden, um bestimmte Antwortheader anzuzeigen. Die Werte dieser Antwortheader geben an, ob Fastly aktiviert ist und ordnungsgemäß funktioniert. Sie können Probleme anhand der Werte von Kopfzeilen und des Cacheverhaltens weiter untersuchen.
exl-id: 725949e9-b69b-456f-9c56-e2163143a71e
feature: Cache, Cloud, Console, Paas
role: Developer
source-git-commit: 586a8c6340bfd2cbf773d1b009d6e106e930117d
workflow-type: tm+mt
source-wordcount: '1207'
ht-degree: 0%

---

# Die schnelle Zwischenspeicherung funktioniert in Adobe Commerce in der Cloud-Infrastruktur nicht

Dieser Artikel enthält eine Fehlerbehebung für das schnelle Zwischenspeichern, das auf Ihrer Site nicht funktioniert. Fastly ist ein CDN- und Caching-Dienst, der in Adobe Commerce in Cloud-Infrastrukturplänen und -Implementierungen enthalten ist. Um zu überprüfen, ob die Fastly-Erweiterung funktioniert, oder um die Fastly-Erweiterung zu debuggen, können Sie den curl-Befehl verwenden, um bestimmte Antwortheader anzuzeigen. Die Werte dieser Antwortheader geben an, ob Fastly aktiviert ist und ordnungsgemäß funktioniert. Sie können Probleme anhand der Werte von Kopfzeilen und des Cacheverhaltens weiter untersuchen.

Diese Informationen helfen Ihnen beim Überprüfen und Testen von Schnellkopfzeilen für Ihre Live-Site und Herkunftsserver.

## Betroffene Versionen

* Adobe Commerce auf Cloud-Infrastruktur
* Fastly 1.2.27 und höher

## Problem

Die Zwischenspeicherung funktioniert möglicherweise nicht für Ihre Live-Site-, Produktions- oder Staging-Umgebungen.

## Ursache

In der Regel funktionieren Konfigurationen, falsche Anmeldeinformationen oder nicht unterstützte Adobe Commerce-Erweiterungen nicht, wenn die schnelle Zwischenspeicherung nicht funktioniert. Wenn Sie Fastly falsch eingerichtet haben oder eine nicht unterstützte Erweiterung verwenden, die Kopfzeilen schneidet, funktioniert das schnelle Zwischenspeichern nicht.

## Mit Befehlen testen und Antwort-Header überprüfen

### Testen mit dem Befehl &quot;dig&quot;

Überprüfen Sie zunächst, ob Kopfzeilen mit einem &quot;dig&quot;-Befehl zur URL vorhanden sind. Geben Sie in einer Terminal-Anwendung die Ziffer `<url>` ein, um zu überprüfen, ob die Fastly-Dienste in den Kopfzeilen angezeigt werden. Weitere Gradungstests finden Sie unter Fastly&#39;s [Testing before change DNS](https://docs.fastly.com/guides/basic-configuration/testing-setup-before-changing-domains).

Beispiel:

* Live-Site: `dig http[s]://<your domain>`
* Staging: `dig http[s]://staging.<your domain>.c.<instanceid>.ent.magento.cloud`
* Produktion: `dig http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud`

### Mit curl testen, Befehl

Verwenden Sie als Nächstes einen curl-Befehl, um zu überprüfen, ob X-Magento-Tags vorhanden sind, und zusätzliche Kopfzeileninformationen. Das Befehlsformat unterscheidet sich bei Staging und Produktion.

Weitere Informationen zu diesen Befehlen erhalten Sie, wenn Sie &quot;`-H "host:URL"`&quot;, &quot;Ersetzen mit Ursprung zum Verbindungsspeicherort&quot;(CNAME-Informationen aus Ihrer OneDrive-Tabelle), &quot;`-k`&quot;ignoriert SSL und &quot;`-v`&quot;liefert ausführliche Antworten. Wenn Kopfzeilen korrekt angezeigt werden, überprüfen Sie die Live-Site und überprüfen Sie die Kopfzeilen erneut.

* Wenn Kopfzeilenprobleme auftreten, wenn die ursprünglichen Server direkt über die Umgehung von Fastly erreicht werden, kann es zu Problemen im Code, mit Erweiterungen oder mit der Infrastruktur kommen.
* Wenn keine Fehler auftreten, die direkt auf die Herkunftsserver gelangen, aber Header fehlen, die die Live-Domäne über Fastly erreichen, kann es zu Fastly-Fehlern kommen.

Überprüfen Sie zunächst Ihre **Live-Site**, um die Antwortheader zu überprüfen. Der Befehl durchläuft die Fastly-Erweiterung, um Antworten zu erhalten. Wenn Sie nicht die richtigen Header erhalten, sollten Sie die Herkunftsserver direkt testen. Dieser Befehl gibt die Werte der Header `Fastly-Magento-VCL-Uploaded` und `X-Cache` zurück.

1. Geben Sie in einem Terminal den folgenden Befehl ein, um Ihre Live-Site-URL zu testen:

   ```
   curl http://<live URL> -vo /dev/null -HFastly-Debug:1 [--resolve]
   ```

   Verwenden Sie `--resolve` nur, wenn Ihre Live-URL nicht mit DNS eingerichtet ist und Sie keine statische Route festgelegt haben. Beispiel:

   ```
   curl http://www.mymagento.biz -vo /dev/null -HFastly-Debug:1
   ```

1. Überprüfen Sie die Antwortheader, um sicherzustellen, dass Fastly funktioniert. Die Ausgabe für diesen Befehl ähnelt der curl-Staging- und -Produktionsumgebung. Beispielsweise sollten die zurückgegebenen eindeutigen Header durch diesen Befehl angezeigt werden:

   ```
   < Fastly-Magento-VCL-Uploaded: yes    < X-Cache: HIT, MISS
   ```

Testen von **Staging** :

```
curl http[s]://staging.<your domain>.c.<instanceid>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

So testen Sie den **Produktionslastausgleich** :

```
curl http[s]://<your domain>.c.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Testen des Knotens **Produktionsursprung** :

```
curl http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Ein direkter Herkunftsknoten:

```
curl http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Wenn Sie beispielsweise über eine öffentliche URL www.mymagento.biz verfügen, geben Sie einen Befehl ähnlich dem folgenden ein, um die Produktions-Site zu testen:

```
curl -k https://www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud -H 'Host: www.mymagento.biz' -vo /dev/null -HFastly-Debug:1
```

### Überprüfen von Antwortheadern

* Überprüfen Sie die zurückgegebenen Antwortheader und -werte:
* Fastly-Magento-VCL-Uploaded sollte vorhanden sein
* X-Magento-Tags sollten zurückgegeben werden
* Fastly-Module-Enabled sollte entweder Ja oder die Versionsnummer der Fastly-Erweiterung sein.
* X-Cache sollte entweder HIT oder HIT sein, HIT
* x-cache-hits sollte 1,1 sein
* Cache-Control: max-age sollte größer als 0 sein
* Pragma sollte zwischengespeichert werden

Das folgende Beispiel zeigt die richtigen Werte für Pragma, X-Magento-Tags und Fastly-Module-Enabled.

Die Ausgabe für curl-Befehle kann lang sein. Im Folgenden finden Sie nur eine Zusammenfassung:

```
* STATE: INIT => CONNECT handle 0x600057800; line 1402 (connection #-5000)
* Rebuilt URL to: https://www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud/
* Added connection 0. The cache now contains 1 members
* Trying 192.0.2.31...
* STATE: CONNECT => WAITCONNECT handle 0x600057800; line 1455 (connection #0)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                             Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0* Connected to www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud (54.229.163.31) port 443 (#0)
* STATE: WAITCONNECT => SENDPROTOCONNECT handle 0x600057800; line 1562 (connection #0)
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0* ALPN, offering h2

  ... portion omitted for brevity ...

< Set-Cookie: mage-messages=%5B%5D; expires=Wed, 22-Nov-2017 17:39:58 GMT; Max-Age=31536000; path=/
< Pragma: cache
< Expires: Wed, 23 Nov 2016 17:39:56 GMT
< Cache-Control: max-age=86400, public, s-maxage=86400, stale-if-error=5, stale-while-revalidate=5
< X-Magento-Tags: cb_welcome_popup store cb cb_store_info_mobile cb_header_promotional_bar cb_store_info cb_discount-promo-bar cpg_2 cb_83 cb_81 cb_84 cb_85 cb_86 cb_87 cb_88 cb_89 p5646 catalog_product p5915 p6040 p6197 p6227 p7095 p6109 p6122 p6331 p7592 p7651 p7690
< Fastly-Module-Enabled: yes
< Strict-Transport-Security: max-age=31536000
    < Content-Security-Policy: upgrade-insecure-requests
< X-Content-Type-Options: nosniff
< X-XSS-Protection: 1; mode=block
< X-Frame-Options: SAMEORIGIN
< X-Platform-Server: i-dff64b52
<
* STATE: PERFORM => DONE handle 0x600057800; line 1955 (connection #0)
* multi_done
  0     0    0     0    0     0      0      0 --:--:--  0:00:02 --:--:--     0
* Connection #0 to host www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud left intact
```

## Auflösen

### Fastly-Module-Enabled ist nicht vorhanden

Wenn Sie in den Antwortheadern kein &quot;Ja&quot;für das Fastly-Module-Enabled erhalten, müssen Sie überprüfen, ob das Fasty-Modul installiert und ausgewählt ist.

Um sicherzustellen, dass Fastly in der Staging- und Produktionsumgebung aktiviert ist, überprüfen Sie die Konfiguration in der Commerce-Admin für jede Umgebung:

1. Melden Sie sich bei der Admin Console für Staging und Produktion über die URL mit /admin (oder die geänderte Admin-URL) an.
1. Navigieren Sie zu Stores > Konfiguration > Erweitert > System . Scrollen Sie nach unten und klicken Sie auf Vollständiger Seiten-Cache.
1. Stellen Sie sicher, dass Fastly CDN ausgewählt ist.
1. Klicken Sie auf Schnelle Konfiguration . Stellen Sie sicher, dass die Fastly Service ID und das Fastly API-Token eingegeben wurden (Ihre Fastly-Anmeldedaten). Stellen Sie sicher, dass Sie die richtigen Anmeldeinformationen für die Staging- und Produktionsumgebung eingegeben haben. Klicken Sie auf Testanmeldeinformationen , um Hilfe zu erhalten.
1. Bearbeiten Sie Ihre Composer.json und stellen Sie sicher, dass das Fasty-Modul in der Version enthalten ist. In dieser Datei sind alle Module mit Versionen aufgeführt.

   * Im Abschnitt &quot;Erforderlich&quot;sollten Sie &quot;fastly/magento2&quot;haben: `<version number>`
   * Im Abschnitt &quot;Repositorys&quot;sollten Sie Folgendes haben:

   ```
   "fastly-magento2": {    "type": "vcs",    "url": "https://github.com/fastly/fastly-magento2.git"    }
   ```

1. Wenn Sie Configuration Management verwenden, sollten Sie über eine Konfigurationsdatei verfügen. Bearbeiten Sie die Datei app/etc/config.app.php (2.0, 2.1) oder app/etc/config.php (2.2) und stellen Sie sicher, dass die Einstellung `'Fastly_Cdn' => 1` korrekt ist. Die Einstellung sollte nicht `'Fastly_Cdn' => 0` sein (d. h. deaktiviert). Wenn Sie die Option Fastly aktiviert haben, löschen Sie die Konfigurationsdatei und führen Sie den Befehl bin/magento magento-cloud:scd-dump aus, um zu aktualisieren. Eine schrittweise Anleitung zu dieser Datei finden Sie unter [Beispiel für die Verwaltung systemspezifischer Einstellungen](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html#manage-the-system-specific-configuration) im Konfigurationshandbuch.

Wenn das Modul nicht installiert ist, müssen Sie in einer Verzweigung [Integrationsumgebung](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) installieren und für Staging und Produktion bereitstellen. Anweisungen finden Sie unter [Schnelles Einrichten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) im Handbuch zu Commerce on Cloud Infrastructure.

### Fastly-Magento-VCL-Uploaded ist nicht vorhanden

Während der Installation und Konfiguration sollten Sie den Fastly VCL hochgeladen haben. Dies sind die Basis-VCL-Snippets, die vom Fastly-Modul bereitgestellt werden, nicht benutzerdefinierte VCL-Snippets, die Sie erstellen. Anweisungen finden Sie unter [Fastly VCL-Snippets hochladen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#upload-vcl-to-fastly) im Handbuch zu Commerce on Cloud Infrastructure.

### X-Cache enthält MISS

Wenn der X-Cache entweder &quot;HIT&quot;, &quot;MISS&quot;oder &quot;MISS&quot;lautet, geben Sie denselben curl-Befehl erneut ein, um sicherzustellen, dass die Seite nicht vor Kurzem aus dem Cache entfernt wurde.

Wenn Sie dasselbe Ergebnis erhalten, verwenden Sie die curl-Befehle und überprüfen Sie die Antwort-Header:

* Pragma is cache
* X-Magento-Tags sind vorhanden
* Cache-Control: max-age ist größer als 0

Wenn das Problem weiterhin besteht, werden diese Kopfzeilen wahrscheinlich von einer anderen Erweiterung zurückgesetzt. Wiederholen Sie das folgende Verfahren in Staging, um Erweiterungen zu deaktivieren, um herauszufinden, welche das Problem verursacht. Nachdem Sie die Erweiterungen gefunden haben, die das Problem verursachen, müssen Sie die Erweiterungen in der Produktion deaktivieren.

1. Um die Erweiterungen zu deaktivieren, führen Sie die Schritte aus, die im Abschnitt [Erweiterungen verwalten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/extensions.html?lang=en#manage-extensions) des Commerce-Handbuchs zur Cloud-Infrastruktur beschrieben werden.
1. Nachdem Sie die Erweiterungen deaktiviert haben, gehen Sie zu **[!UICONTROL System]** > **[!UICONTROL Tools]** > **[!UICONTROL Cache Management]**.
1. Klicken Sie auf **[!UICONTROL Flush Magento Cache]**.
1. Aktivieren Sie jetzt jeweils eine Erweiterung, speichern Sie die Konfiguration und leeren Sie den Cache.
1. Probieren Sie die curl-Befehle aus und überprüfen Sie die Antwortheader.
1. Wiederholen Sie die Schritte 4 und 5, um die curl-Befehle zu aktivieren und zu testen. Wenn die Schnellkopfzeilen nicht mehr angezeigt werden, haben Sie die Erweiterung gefunden, die Probleme mit Fastly verursacht hat.

Wenn Sie die Erweiterung isolieren, die Fastly-Header zurücksetzt, wenden Sie sich an den Entwickler der Erweiterung, um weitere Unterstützung zu erhalten. Für Entwickler von Drittanbietererweiterungen können keine Fehlerbehebungen oder Updates bereitgestellt werden, um mit dem Fastly-Caching zu arbeiten.

## Weitere Informationen finden Sie in unserer Entwicklerdokumentation:

* [Info über Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)
* [Schnelles Einrichten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html)
* [Benutzerdefinierte schnelle VCL-Snippets](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html)
