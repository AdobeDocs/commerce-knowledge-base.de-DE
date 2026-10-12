---
title: 'Bereitstellungsfehler: *Fehler 7 beim Herunterladen … Port 443: Verbindung verweigert*'
description: 'Dieser Artikel bietet eine Lösung für den Bereitstellungsfehler: *„Fehler 7 beim Herunterladen von … Port 443: Verbindung verweigert“*.'
exl-id: 520cf50f-3682-441d-87a7-8e05301a2b0c
feature: Cache, Deploy
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%
---
# Bereitstellungsfehler: *Fehler 7 beim Herunterladen von … Port 443: Verbindung verweigert*

Dieser Artikel bietet eine Lösung für das Problem, wenn die Bereitstellung mit der folgenden Fehlermeldung fehlschlägt:

```bash
W: In CurlDownloader.php line 370:
W:
W:   curl error 7 while downloading https://repo.packagist.org/p2/magento/module
W:   -sitemap.json: Failed to connect to repo.packagist.org port 443: Connection
W:    refused
```

## Betroffene Versionen

Adobe Commerce auf Cloud-Infrastruktur, [alle unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problem

Die Bereitstellung schlägt mit der **curl error 7)**.

<u>Schritte zur Reproduktion</u>:

Trigger einer -Bereitstellung.

<u>Erwartetes </u>:

Die Bereitstellung war erfolgreich.

<u>Tatsächliches </u>:

Die Bereitstellung schlägt fehl und die folgende Fehlermeldung wird im Bereitstellungsprotokoll angezeigt: *cURL-Fehler 7 beim Herunterladen von … Port 443* Verbindung verweigert.

## Ursache

Dies kann darauf zurückzuführen sein, dass die Cache-Verbindung mit dem Repository verloren geht.

## Lösung

Bitten Sie einen Superbenutzer des Projekts, diesen Befehl auszuführen:

```bash
magento-cloud project:clear-build-cache -p <project ID>
```

Informationen dazu, wer im Projekt ein Super-Anwender ist, finden Sie unter [Anzeigen der Projektrolle eines Anwenders](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=en#view-a-user’s-project-role) im Handbuch zu Commerce in Cloud-Infrastruktur .

## Empfohlene Lektüre

* Fehlerbehebung bei der Bereitstellung von [Adobe Commerce](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-29640).
* Auf [Adobe Commerce in Cloud-Repository konnte nicht zugegriffen werden: Fehler „403 Verboten“ oder „404 Nicht gefunden“ bei der Bereitstellung](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html).
* [Bereitstellung schlägt mit „Fehler beim Erstellen des Projekts: Der Build-Hook ist mit Status-Code 1 fehlgeschlagen“](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-fails-with-error-building-project-the-build-hook-failed-with-status-code-1.html).
