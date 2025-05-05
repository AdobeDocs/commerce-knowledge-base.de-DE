---
title: 'ACSD-47076: [!DNL Vimeo] Videos können nicht in der Storefront wiedergegeben werden'
description: Wenden Sie den Patch ACSD-47076 an, um das Adobe Commerce-Problem zu beheben [!DNL Vimeo]  bei dem Videos nicht in der Storefront wiedergegeben werden können.
exl-id: 52161c0d-3d51-45a3-ba41-36f955df0bea
feature: Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# ACSD-47076: [!DNL Vimeo] Videos können nicht in der Storefront abgespielt werden

Mit dem Patch ACSD-47076 wird das Problem behoben, dass [!DNL Vimeo] Videos nicht in der Storefront wiedergegeben werden können. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 installiert ist. Die Patch-ID ist ACSD-47076. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.3-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

[!DNL Vimeo] Videos können nicht in der Storefront wiedergegeben werden.

<u>Schritte zur Reproduktion</u>:

1. Hinzufügen eines [!DNL Vimeo] Videos zu einem Produkt in der Commerce-[!UICONTROL Admin] > **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > Produktbearbeitungsseite > **[!UICONTROL Images and Videos]**.
1. Öffnen Sie das Produkt in der Storefront und spielen Sie das Video ab.

<u>Erwartete Ergebnisse</u>:

Das [!DNL Vimeo] Video kann abgespielt werden.

<u>Tatsächliche Ergebnisse</u>:

Das [!DNL Vimeo] Video kann nicht in der Storefront wiedergegeben werden.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
