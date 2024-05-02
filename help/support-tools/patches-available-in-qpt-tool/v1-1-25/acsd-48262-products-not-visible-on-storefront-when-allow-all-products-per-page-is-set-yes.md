---
title: '"ACSD-48262: Produkte, die nicht auf der Storefront sichtbar sind, wenn [!UICONTROL Allow All Products Per Page] festgelegt ist [!UICONTROL Yes]'''
description: Wenden Sie den Patch ACSD-48262 an, um das Adobe Commerce-Problem zu beheben, bei dem Produkte auf der Storefront nicht sichtbar sind, wenn die [!UICONTROL Allow All Products Per Page] festgelegt ist auf [!UICONTROL Yes].
exl-id: 327cad03-441d-4adb-8a10-802f06d3fcd1
feature: Admin Workspace, Cache, Categories, Orders, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-48262: Produkte, die nicht auf der Storefront sichtbar sind, wenn [!UICONTROL Allow All Products Per Page] festgelegt ist *[!UICONTROL Yes]*

Der Patch ACSD-48262 behebt das Problem, dass Produkte nicht auf der Storefront sichtbar sind, wenn die [!UICONTROL Allow All Products Per Page] festgelegt ist auf *[!UICONTROL Yes]*. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 ist installiert. Die Patch-ID ist ACSD-48262. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) >=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Patch ACSD-48262 behebt das Problem, dass Produkte nicht auf der Storefront sichtbar sind, wenn die [!UICONTROL Allow All Products Per Page] festgelegt ist auf *[!UICONTROL Yes]*.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine Testkategorie.
1. Erstellen Sie ein Testprodukt in der Testkategorie.
1. Durchsuchen Sie das Produkt, um die Kategorieseite auf der Storefront zu testen und sicherzustellen, dass das Produkt sichtbar ist.
1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** und legen Sie die [!UICONTROL Allow All Products Per Page] Einstellung auf *[!UICONTROL Yes]*.
1. Löschen Sie Cache.
1. Überprüfen Sie die Kategorieseite auf der Storefront.

<u>Erwartete Ergebnisse</u>:

Das Produkt ist sichtbar.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt ist nicht sichtbar.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
