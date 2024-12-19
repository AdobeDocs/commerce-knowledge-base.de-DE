---
title: 'ACSD-48262: Produkte werden in der Storefront nicht angezeigt, wenn [!UICONTROL Allow All Products Per Page] festgelegt ist [!UICONTROL Yes]'
description: Wenden Sie den ACSD-48262 Patch an, um das Adobe Commerce-Problem zu beheben, dass Produkte in der Storefront nicht angezeigt werden, wenn die [!UICONTROL Allow All Products Per Page] auf [!UICONTROL Yes] festgelegt ist.
exl-id: 327cad03-441d-4adb-8a10-802f06d3fcd1
feature: Admin Workspace, Cache, Categories, Orders, Products, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-48262: Produkte werden in der Storefront nicht angezeigt, wenn [!UICONTROL Allow All Products Per Page] festgelegt ist *[!UICONTROL Yes]*

Mit dem Patch ACSD-48262 wird das Problem behoben, dass Produkte nicht in der Storefront sichtbar sind, wenn die [!UICONTROL Allow All Products Per Page] auf *[!UICONTROL Yes]* festgelegt ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 installiert ist. Die Patch-ID ist ACSD-48262. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) >=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Mit dem Patch ACSD-48262 wird das Problem behoben, dass Produkte nicht in der Storefront sichtbar sind, wenn die [!UICONTROL Allow All Products Per Page] auf *[!UICONTROL Yes]* festgelegt ist.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine Testkategorie.
1. Erstellen Sie ein Testprodukt in der Testkategorie.
1. Durchsuchen Sie die Seite mit der Kategorie „Produkt testen“ in der Storefront und stellen Sie sicher, dass das Produkt sichtbar ist.
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** und setzen Sie die [!UICONTROL Allow All Products Per Page] auf *[!UICONTROL Yes]*.
1. Cache löschen.
1. Kategorieseite in der Storefront überprüfen.

<u>Erwartete Ergebnisse</u>:

Das Produkt ist sichtbar.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt ist nicht sichtbar.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool].
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
