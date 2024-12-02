---
title: 'Bereitstellungsfehler: *Fehler 7 beim Herunterladen ... Port 443: Verbindung verweigert*'
description: 'Dieser Artikel bietet eine Lösung für den Bereitstellungsfehler: *"Fehler 7 beim Herunterladen ... Port 443: Verbindung verweigert"*.'
exl-id: 520cf50f-3682-441d-87a7-8e05301a2b0c
feature: Cache, Deploy
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# Bereitstellungsfehler: *Fehler 7 beim Herunterladen ... Port 443: Verbindung verweigert*

Dieser Artikel enthält eine Fehlerbehebung für das Problem, das bei einer fehlgeschlagenen Bereitstellung mit der folgenden Fehlermeldung auftritt:

```bash
W: In CurlDownloader.php line 370:
W:
W:   curl error 7 while downloading https://repo.packagist.org/p2/magento/module
W:   -sitemap.json: Failed to connect to repo.packagist.org port 443: Connection
W:    refused
```

## Betroffene Versionen

Adobe Commerce in der Cloud-Infrastruktur, [alle unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problem

Die Bereitstellung schlägt mit der Meldung **curl error 7** fehl.

<u>Zu reproduzierende Schritte</u>:

Trigger einer Bereitstellung.

<u>Erwartetes Verhalten</u>:

Die Implementierung ist erfolgreich.

<u>Tatsächliches Verhalten</u>:

Die Bereitstellung schlägt fehl, und der folgende Fehler: *curl error 7 while download ... port 443: Connection refused* wird im Bereitstellungsprotokoll angezeigt.

## Ursache

Dies kann daran liegen, dass die Cache-Verbindung mit dem Repo verloren geht.

## Lösung

Bitten Sie einen Superuser im Projekt, diesen Befehl auszuführen:

```bash
magento-cloud project:clear-build-cache -p <project ID>
```

Informationen dazu, wer im Projekt ein Superuser ist, finden Sie unter [Anzeigen der Projektrolle eines Benutzers](/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=en#view-a-user’s-project-role) im Commerce on Cloud Infrastructure Guide.

## Empfohlene Lesbarkeit

* [Fehlerbehebung bei der Adobe Commerce-Bereitstellung](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-deployment-troubleshooter.html).
* [Auf Adobe Commerce in Cloud Repo konnte nicht zugegriffen werden: Fehler 403 Verboten oder 404 Nicht gefunden bei Bereitstellung von ](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html).
* [Die Bereitstellung schlägt mit &quot;Fehler beim Erstellen des Projekts: Der Build-Hook ist mit Status-Code 1 fehlgeschlagen&quot;](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-fails-with-error-building-project-the-build-hook-failed-with-status-code-1.html) fehl.
