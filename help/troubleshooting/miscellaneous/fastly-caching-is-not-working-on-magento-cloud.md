---
title: Fastly-Caching funktioniert nicht in Adobe Commerce auf Cloud-Infrastruktur
description: Dieser Artikel bietet eine Fehlerbehebung für Fälle, in denen Fastly-Caching auf Ihrer Site nicht funktioniert. Fastly ist ein CDN- und Caching-Service, der in Adobe Commerce zu Cloud-Infrastrukturplänen und -Implementierungen enthalten ist. Um zu überprüfen, ob die Fastly-Erweiterung funktioniert, oder um die Fastly-Erweiterung zu debuggen, können Sie den curl-Befehl verwenden, um bestimmte Antwort-Header anzuzeigen. Die Werte dieser Antwort-Header geben an, ob Fastly aktiviert ist und ordnungsgemäß funktioniert. Sie können Probleme basierend auf den Werten der -Kopfzeilen und dem Caching-Verhalten weiter untersuchen.
exl-id: 725949e9-b69b-456f-9c56-e2163143a71e
feature: Cache, Cloud, Console, Paas
role: Developer
source-git-commit: 139c2836ba36686357c7a5458a36550c7b1273c1
workflow-type: tm+mt
source-wordcount: '1207'
ht-degree: 0%

---

# Fastly-Caching funktioniert nicht in Adobe Commerce auf Cloud-Infrastruktur

Dieser Artikel bietet eine Fehlerbehebung für Fälle, in denen Fastly-Caching auf Ihrer Site nicht funktioniert. Fastly ist ein CDN- und Caching-Service, der in Adobe Commerce zu Cloud-Infrastrukturplänen und -Implementierungen enthalten ist. Um zu überprüfen, ob die Fastly-Erweiterung funktioniert, oder um die Fastly-Erweiterung zu debuggen, können Sie den curl-Befehl verwenden, um bestimmte Antwort-Header anzuzeigen. Die Werte dieser Antwort-Header geben an, ob Fastly aktiviert ist und ordnungsgemäß funktioniert. Sie können Probleme basierend auf den Werten der -Kopfzeilen und dem Caching-Verhalten weiter untersuchen.

Diese Informationen helfen Ihnen beim Überprüfen und Testen von Fastly-Kopfzeilen für Ihre Live-Site und Ihre Ursprungs-Server.

## Betroffene Versionen

* Adobe Commerce auf Cloud-Infrastruktur
* Fastly 1.2.27 und höher

## Problem

Das Caching funktioniert möglicherweise nicht für Ihre Live-Site-, Produktions- oder Staging-Umgebung.

## Ursache

Normalerweise sind Konfigurationen, falsche Anmeldeinformationen oder nicht unterstützte Adobe Commerce-Erweiterungen das Problem, dass die Fastly-Zwischenspeicherung nicht funktioniert. Wenn Sie Fastly falsch eingerichtet haben oder eine nicht unterstützte Erweiterung verwenden, die Header abschneidet, funktioniert die Fastly-Zwischenspeicherung nicht.

## Testen mit Befehlen und Überprüfen der Antwort-Header

### Testen mit dem Befehl „dig“

Suchen Sie zunächst nach Kopfzeilen, indem Sie einen dig-Befehl an die URL senden. Geben Sie in einer Terminal-Anwendung dig `<url>` ein, um zu überprüfen, ob die Fastly-Services in den Kopfzeilen angezeigt werden. Weitere Prüfungen finden Sie unter Fastly&#39;s [Testing before changing DNS](https://docs.fastly.com/guides/basic-configuration/testing-setup-before-changing-domains).

Beispiel:

* Live-Site: `dig http[s]://<your domain>`
* Staging: `dig http[s]://staging.<your domain>.c.<instanceid>.ent.magento.cloud`
* Produktion: `dig http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud`

### Testen mit dem curl-Befehl

Verwenden Sie als Nächstes einen curl-Befehl, um zu überprüfen, ob X-Magento-Tags und zusätzliche Header-Informationen vorhanden sind. Das Befehlsformat für die Staging- und Produktionsumgebung ist unterschiedlich.

Weitere Informationen zu diesen Befehlen erhalten Sie, wenn Sie Fastly umgehen, wenn Sie `-H "host:URL"` injizieren, durch den Ursprung zum Verbindungsort ersetzen (CNAME-Informationen aus Ihrer OneDrive-Tabelle), SSL ignorieren `-k` ausführliche Antworten `-v`. Wenn Kopfzeilen korrekt angezeigt werden, überprüfen Sie die Live-Site und überprüfen Sie die Kopfzeilen erneut.

* Wenn beim direkten Aufrufen der ursprünglichen Server unter Umgehung von Fastly Kopfzeilenprobleme auftreten, kann es zu Problemen in Ihrem Code, mit Erweiterungen oder mit der Infrastruktur kommen.
* Wenn Sie auf keine Fehler stoßen, die direkt auf die Ursprungs-Server treffen, aber Kopfzeilen fehlen, die die Live-Domain über Fastly treffen, können Fastly-Fehler auftreten.

Überprüfen Sie zunächst Ihre **Live-Site**, um die Antwort-Header zu überprüfen. Der Befehl durchläuft die Fastly-Erweiterung, um Antworten zu erhalten. Wenn Sie nicht die richtigen Kopfzeilen erhalten, sollten Sie die Ursprungs-Server direkt testen. Dieser Befehl gibt die Werte der `Fastly-Magento-VCL-Uploaded`- und `X-Cache`-Kopfzeilen zurück.

1. Geben Sie in einem Terminal den folgenden Befehl ein, um Ihre Live-Site-URL zu testen:

   ```
   curl http://<live URL> -vo /dev/null -HFastly-Debug:1 [--resolve]
   ```

   Verwenden Sie `--resolve` nur, wenn Ihre Live-URL nicht mit DNS eingerichtet ist und Sie keine statische Route festgelegt haben. Beispiel:

   ```
   curl http://www.mymagento.biz -vo /dev/null -HFastly-Debug:1
   ```

1. Überprüfen Sie die Antwort-Header, um sicherzustellen, dass Fastly funktioniert. Die Ausgabe für diesen Befehl ähnelt cURL-Staging und -Produktion. Sie sollten beispielsweise die von diesem Befehl zurückgegebenen eindeutigen Kopfzeilen sehen:

   ```
   < Fastly-Magento-VCL-Uploaded: yes    < X-Cache: HIT, MISS
   ```

Testen von **Staging**:

```
curl http[s]://staging.<your domain>.c.<instanceid>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

So testen Sie **Produktionslastenausgleich** :

```
curl http[s]://<your domain>.c.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

So testen Sie **Produktionsursprungsknoten** :

```
curl http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Ein direkter Ursprungsknoten:

```
curl http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Wenn Sie beispielsweise über die öffentliche URL www.mymagento.biz verfügen, geben Sie einen Befehl ähnlich dem folgenden ein, um die Produktions-Site zu testen:

```
curl -k https://www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud -H 'Host: www.mymagento.biz' -vo /dev/null -HFastly-Debug:1
```

### Antwort-Header überprüfen

* Überprüfen Sie die zurückgegebenen Antwortkopfzeilen und -werte:
* Fastly-Magento-VCL-Uploaded sollte vorhanden sein
* X-Magento-Tags sollten zurückgegeben werden
* Fastly-Module-Enabled sollte entweder Ja oder die Fastly-Erweiterungsversionsnummer sein
* X-Cache sollte entweder HIT oder HIT, HIT sein
* X-Cache-Treffer sollten 1,1 sein
* Cache-Steuerung: max-age sollte größer als 0 sein
* Pragma sollte zwischengespeichert werden

Das folgende Beispiel zeigt die richtigen Werte für Pragma, X-Magento-Tags und Fastly-Module-Enabled.

Die Ausgabe für cURL-Befehle kann sehr lang sein. Im Folgenden finden Sie nur eine Zusammenfassung:

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

## Lösen

### Fastly-Module-Enabled ist nicht vorhanden

Wenn Sie in den Antwort-Headern kein „Ja“ für das Fastly-Modul-aktivierte erhalten, müssen Sie überprüfen, ob das Fasty-Modul installiert und ausgewählt ist.

Um zu überprüfen, ob Fastly in Staging und Produktion aktiviert ist, überprüfen Sie die Konfiguration in der Commerce Admin für jede Umgebung:

1. Melden Sie sich bei der Admin Console für Staging und Produktion mit der URL unter /admin (oder der geänderten Admin-URL) an.
1. Navigieren Sie zu Stores > Konfiguration > Erweitert > System. Scrollen Sie und klicken Sie auf Vollständiger Seitencache.
1. Stellen Sie sicher, dass Fastly CDN ausgewählt ist.
1. Klicken Sie auf Fastly Configuration. Stellen Sie sicher, dass die Fastly Service-ID und das Fastly-API-Token eingegeben werden (Ihre Fastly-Anmeldedaten). Stellen Sie sicher, dass Sie die richtigen Anmeldeinformationen für die Staging- und Produktionsumgebung eingegeben haben. Klicken Sie auf Testanmeldeinformationen , um Hilfe zu erhalten.
1. Bearbeiten Sie Ihre composer.json und stellen Sie sicher, dass das Fasty-Modul in der Version enthalten ist. Diese Datei enthält alle Module, die mit Versionen aufgelistet sind.

   * Im Abschnitt „erforderlich“ sollten Sie „fastly/magento2“ haben: `<version number>`
   * Im Abschnitt „Repositorys“ sollten Sie über Folgendes verfügen:

   ```
   "fastly-magento2": {    "type": "vcs",    "url": "https://github.com/fastly/fastly-magento2.git"    }
   ```

1. Wenn Sie die Konfigurationsverwaltung verwenden, sollten Sie über eine Konfigurationsdatei verfügen. Bearbeiten Sie die Datei app/etc/config.app.php (2.0, 2.1) oder app/etc/config.php (2.2) und stellen Sie sicher, dass die Einstellung `'Fastly_Cdn' => 1` korrekt ist. Die Einstellung sollte nicht `'Fastly_Cdn' => 0` sein (d. h. deaktiviert). Wenn Sie Fastly aktiviert haben, löschen Sie die Konfigurationsdatei und führen Sie den Befehl bin/magento-cloud:scd-dump aus, um sie zu aktualisieren. Eine Anleitung für diese Datei finden Sie [Beispiel für die Verwaltung systemspezifischer Einstellungen](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html?lang=de#manage-the-system-specific-configuration) im Konfigurationshandbuch.

Wenn das Modul nicht installiert ist, müssen Sie es in einer Verzweigung des Typs [Integrationsumgebung](https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-27242) installieren und in der Staging- und Produktionsumgebung bereitstellen. Anweisungen [&#x200B; Handbuch zu Commerce &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=de) Cloud-Infrastruktur finden Sie unter „Schnell einrichten“.

### Fastly-Magento-VCL-Uploaded ist nicht vorhanden

Während der Installation und Konfiguration sollten Sie die Fastly-VCL hochgeladen haben. Dies sind die grundlegenden VCL-Snippets, die vom Fastly-Modul bereitgestellt werden, und keine benutzerdefinierten VCL-Snippets, die Sie erstellen. Anweisungen finden Sie unter [Hochladen von Fastly VCL-Snippets](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=de#upload-vcl-to-fastly) im Handbuch Commerce on Cloud Infrastructure .

### X-Cache enthält MISS

Wenn X-Cache entweder HIT, MISS oder MISS, MISS ist, geben Sie denselben curl-Befehl erneut ein, um sicherzustellen, dass die Seite nicht kürzlich aus dem Cache entfernt wurde.

Wenn Sie dasselbe Ergebnis erhalten, verwenden Sie die curl-Befehle und überprüfen Sie die Antwort-Header:

* Pragma ist Cache
* X-Magento-Tags existiert
* Cache-Steuerung: max-age ist größer als 0

Wenn das Problem weiterhin besteht, wird diese Kopfzeile wahrscheinlich von einer anderen Erweiterung zurückgesetzt. Wiederholen Sie das folgende Verfahren in Staging , um Erweiterungen zu deaktivieren und herauszufinden, welche die Ursache des Problems sind. Nachdem Sie die Erweiterung(en) gefunden haben, die das Problem verursachen, müssen Sie die Erweiterung(en) in der Produktionsumgebung deaktivieren.

1. Um die Erweiterungen zu deaktivieren, führen Sie die Schritte aus, die im Abschnitt [Erweiterungen verwalten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/extensions.html?lang=de#manage-extensions) des Handbuchs zu Commerce in Cloud-Infrastrukturen beschrieben sind.
1. Nachdem Sie die Erweiterungen deaktiviert haben, navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Tools]** > **[!UICONTROL Cache Management]**.
1. Klicken Sie auf **[!UICONTROL Flush Magento Cache]**.
1. Aktivieren Sie jetzt jeweils eine Erweiterung, speichern Sie die Konfiguration und leeren Sie den Cache.
1. Verwenden Sie die cURL-Befehle und überprüfen Sie die Antwort-Header.
1. Wiederholen Sie die Schritte 4 und 5, um die cURL-Befehle zu aktivieren und zu testen. Wenn die Fastly-Kopfzeilen nicht mehr angezeigt werden, haben Sie festgestellt, dass die Erweiterung Probleme mit Fastly verursacht.

Wenn Sie die Erweiterung isolieren, die Fastly-Kopfzeilen zurücksetzt, wenden Sie sich an den Entwickler der Erweiterung, um weitere Hilfe zu erhalten. Wir können keine Fehlerbehebungen oder Aktualisierungen für Entwickler von Drittanbietererweiterungen bereitstellen, um mit Fastly Caching zu arbeiten.

## Weitere Informationen finden Sie in unserer Entwicklerdokumentation:

* [Über Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html?lang=de)
* [Schnell einrichten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=de)
* [Benutzerdefinierte Fastly VCL-Snippets](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html?lang=de)
