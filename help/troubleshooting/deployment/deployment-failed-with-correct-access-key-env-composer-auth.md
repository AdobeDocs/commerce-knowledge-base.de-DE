---
title: Die Bereitstellung schlägt mit den richtigen Zugriffsschlüsseln in env:COMPOSER_AUTH oder auth.json fehl
description: 'Dieser Artikel bietet eine Lösung für das Problem, wenn die Bereitstellung mit dem folgenden Fehler fehlschlägt: „Die Datei https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip konnte nicht heruntergeladen werden (HTTP/1.1 404 Not Found)“.'
feature: Deploy
role: Admin
exl-id: a18f4213-7381-4001-a5a0-3f8db4525469
source-git-commit: 2a1c97c65282d03010bffabbcd2d1be7fb9ff9a6
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# Die Bereitstellung schlägt mit den richtigen Zugriffsschlüsseln in env:COMPOSER_AUTH oder auth.json fehl

Dieser Artikel bietet eine Lösung für das Problem, wenn Ihre Bereitstellung mit einem Fehler wie dem folgenden im [Bereitstellungsprotokoll“ fehlschlägt](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log):

```
W:   [Composer\Downloader\TransportException]
W:   The "https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip" file could not be downloaded (HTTP/1.1 404 Not Found)
```

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur 2.4.x

## Problem

<u>Schritte zur Reproduktion</u>:

Versuchen Sie, bereitzustellen.

<u>Erwartete Ergebnisse</u>:

Sie haben erfolgreich bereitgestellt.

<u>Tatsächliche Ergebnisse</u>:

>[!NOTE]
>
>Dies ist ein Beispielfehler. Je nachdem, welche Adobe Commerce-Version Sie bereitstellen, wird möglicherweise eine Fehlermeldung angezeigt, die auf eine andere Datei verweist.

Die Bereitstellung ist nicht erfolgreich. Es wird ein Fehler wie *Die Datei &quot;https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip&quot; konnte nicht heruntergeladen werden (HTTP/1.1 404 Not Found)* im [Bereitstellungsprotokoll](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log) angezeigt.

### Ursache

Die angegebenen Composer-Zugriffsschlüssel an einem dieser Speicherorte haben möglicherweise keinen Zugriff auf den Code:

* in der Variablen `env:COMPOSER_AUTH` auf Projektebene
* in der `auth.json file`, die Vorrang vor der Variablen `env:COMPOSER_AUTH` hat.

### Lösung

Aktualisieren Sie die Variable `env:COMPOSER_AUTH` auf Projektebene und stellen Sie sicher, dass sie mit Schlüsseln konfiguriert ist, die Zugriff auf den Code haben.

Anweisungen hierzu finden Sie unter [Variablenebenen](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/configure/env/variable-levels) im Handbuch zu Commerce in Cloud-Infrastrukturen.

## Verwandtes Lesen

* [Zugriff auf Adobe Commerce auf Cloud-Repository nicht möglich: Fehler „403 Verboten“ oder „404 Nicht gefunden“ bei der Bereitstellung](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html)
* [Bereitstellungsfehler: Fehler 7 beim Herunterladen von … Port 443: Verbindung verweigert](/help/troubleshooting/deployment/deployment-error-downloading-connection-refused-adobe-commerce.md)
