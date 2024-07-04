---
title: Die Bereitstellung schlägt mit den richtigen Zugriffsschlüsseln in env:COMPOSER_AUTH oder auth.json fehl
description: 'Dieser Artikel bietet eine Lösung für das Problem, wenn die Bereitstellung mit dem folgenden Fehler fehlschlägt: "Die Datei https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip konnte nicht heruntergeladen werden (HTTP/1.1 404 Not Found)".'
feature: Deploy
role: Admin
exl-id: a18f4213-7381-4001-a5a0-3f8db4525469
source-git-commit: 9f9dc8374bb681398ed1c295ac15679553cfc74e
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---

# Die Bereitstellung schlägt mit den richtigen Zugriffsschlüsseln in env:COMPOSER_AUTH oder auth.json fehl

Dieser Artikel bietet eine Lösung für das Problem, wenn Ihre Bereitstellung mit einem Fehler wie dem folgenden in der Variablen [Bereitstellungsprotokoll](/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log):

```
W:   [Composer\Downloader\TransportException]
W:   The "https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip" file could not be downloaded (HTTP/1.1 404 Not Found)
```

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur 2.4.x

## Problem

<u>Zu reproduzierende Schritte</u>:

Versuchen Sie, sie bereitzustellen.

<u>Erwartete Ergebnisse</u>:

Sie können die Bereitstellung erfolgreich durchführen.

<u>Tatsächliche Ergebnisse</u>:

>[!NOTE]
>
>Dies ist ein Beispielfehler. Möglicherweise wird eine Fehlermeldung angezeigt, die eine andere Datei angibt (je nachdem, welche Adobe Commerce-Version Sie bereitstellen).

Sie werden nicht erfolgreich bereitgestellt. Sie sehen einen Fehler wie *Die Datei &quot;https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip&quot; konnte nicht heruntergeladen werden (HTTP/1.1 404 Not Found)* im [Bereitstellungsprotokoll](/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log).

### Ursache

Die in einem dieser Speicherorte gefundenen Zugriffsschlüssel des Composers haben möglicherweise keinen Zugriff auf den Code:

* im `env:COMPOSER_AUTH` auf Projektebene
* im `auth.json file`, der Vorrang vor der `env:COMPOSER_AUTH` -Variable.

### Lösung

Aktualisieren Sie die `env:COMPOSER_AUTH` auf der Projektebene und stellen Sie sicher, dass sie mit Schlüsseln konfiguriert ist, die Zugriff auf den Code haben.

Eine Anleitung finden Sie unter [Variablenebenen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/variable-levels) in Commerce on Cloud Infrastructure Guide.

## Verwandtes Lesen

* [Auf Adobe Commerce on Cloud Repo konnte nicht zugegriffen werden: Fehler 403 Verboten oder 404 Nicht gefunden bei Bereitstellung](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html)
* [Bereitstellungsfehler: Fehler 7 beim Herunterladen ... Port 443: Verbindung verweigert](/help/troubleshooting/deployment/deployment-error-downloading-connection-refused-adobe-commerce.md)
