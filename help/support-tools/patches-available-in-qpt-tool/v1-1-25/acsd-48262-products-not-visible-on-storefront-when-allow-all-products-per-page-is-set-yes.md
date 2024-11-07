---
title: "ACSD-48262: Produkte, die auf der Storefront nicht sichtbar sind, wenn [!UICONTROL Allow All Products Per Page] auf [!UICONTROL Yes] gesetzt ist."
description: Wenden Sie den Patch ACSD-48262 an, um das Adobe Commerce-Problem zu beheben, bei dem Produkte nicht auf der Storefront sichtbar sind, wenn die Einstellung [!UICONTROL Allow All Products Per Page] auf [!UICONTROL Yes] gesetzt ist.
exl-id: 327cad03-441d-4adb-8a10-802f06d3fcd1
feature: Admin Workspace, Cache, Categories, Orders, Products, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-48262: Produkte sind auf der Storefront nicht sichtbar, wenn [!UICONTROL Allow All Products Per Page] auf *[!UICONTROL Yes]* gesetzt ist

Der Patch ACSD-48262 behebt das Problem, dass Produkte nicht auf der Storefront sichtbar sind, wenn die Einstellung [!UICONTROL Allow All Products Per Page] auf *[!UICONTROL Yes]* gesetzt ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 installiert ist. Die Patch-ID ist ACSD-48262. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) >=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Patch ACSD-48262 behebt das Problem, dass Produkte nicht auf der Storefront sichtbar sind, wenn die Einstellung [!UICONTROL Allow All Products Per Page] auf *[!UICONTROL Yes]* gesetzt ist.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine Testkategorie.
1. Erstellen Sie ein Testprodukt in der Testkategorie.
1. Durchsuchen Sie das Produkt, um die Kategorieseite auf der Storefront zu testen und sicherzustellen, dass das Produkt sichtbar ist.
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** und legen Sie die Einstellung [!UICONTROL Allow All Products Per Page] auf *[!UICONTROL Yes]* fest.
1. Löschen Sie Cache.
1. Überprüfen Sie die Kategorieseite auf der Storefront.

<u>Erwartete Ergebnisse</u>:

Das Produkt ist sichtbar.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt ist nicht sichtbar.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
