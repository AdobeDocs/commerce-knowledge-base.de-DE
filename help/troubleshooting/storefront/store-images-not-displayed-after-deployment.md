---
title: Bilder speichern, die nach der Bereitstellung nicht angezeigt werden
description: Dieser Artikel bietet eine Lösung für Fälle, in denen Bilder nach der Bereitstellung nicht korrekt angezeigt werden.
exl-id: 7e6bcebd-edff-437a-9103-2743443d2ed9
feature: Cache, Categories, Deploy, Storefront
role: Admin
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%
---
# Bilder speichern, die nach der Bereitstellung nicht angezeigt werden

Dieser Artikel bietet eine Lösung für Fälle, in denen Bilder nach der Bereitstellung nicht korrekt angezeigt werden.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x

## Problem

Wenn Sie ein Storefront-Design mit einer Bildgrößenanpassung verwenden, werden die Bilder bei der Bereitstellung nicht auf den Katalogseiten angezeigt oder verschwinden nicht.

## Ursache

Dies kann durch Laden der Bilder aus dem Cache verursacht werden.

## Lösung

In diesem Fall können Sie den Magento-Befehl verwenden, um den Bild-Cache neu zu generieren und die Bilder korrekt anzuzeigen.

Dazu benötigen Sie die SSH-Informationen und die Store-URL, die über die [Cloud-Konsole“ verfügbar &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=de).

1. SSH zu Ihrem Projekt, das eine Quelle für den [Datenbank-Dump](/help/how-to/general/create-database-dump-on-cloud.md) war, wie unter [SSH in &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/secure-connections) in unserer Entwicklerdokumentation beschrieben.
1. Generieren Sie den Bild-Cache neu, indem Sie Folgendes ausführen:

   ```bash
   php bin/magento catalog:images:resize
   ```

1. Testen Sie die Kategorieseiten über die Store-URL.
