---
title: 'ACSD-51265: Optimieren der Neuindizierung für gebündelte Produkte'
description: Wenden Sie den Patch ACSD-51265 an, um das Adobe Commerce-Problem zu beheben, bei dem die Neuindizierungsleistung von „CATALOG_PRODUCT_PRICE“ niedrig ist, wenn das System zu viele gebündelte Produkte enthält.
feature: Products, Price Indexer
role: Admin
exl-id: ddf23c19-b1ed-4064-adbc-58707eb63cc9
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# ACSD-51265: Optimieren der Neuindizierung für gebündelte Produkte

Mit dem Patch ACSD-51265 wird das Problem behoben, dass die `catalog_product_price` Neuindizierungsleistung gering ist, wenn das System zu viele gebündelte Produkte enthält. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-51265. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Neuindizierungsleistung des Katalogproduktpreises ist niedrig, wenn das System zu viele gebündelte Produkte enthält.

<u>Schritte zur Reproduktion</u>:

1. Generieren Sie einen Katalog mit mindestens *10.000* gebündelten Produkten mit dynamischen Preisoptionen.
1. Neuindizierung des Produktpreises ausführen.

<u>Erwartete Ergebnisse</u>

Die Neuindizierung des Produktpreises dauert weniger als 15 Minuten.

<u>Tatsächliche Ergebnisse</u>

Die Neuindizierung von Produktpreisen dauert mehr als eine Stunde.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
