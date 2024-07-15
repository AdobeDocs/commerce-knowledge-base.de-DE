---
title: "ACSD-54319: Produktpreis zeigt null im *[!UICONTROL Products in Carts]* Bericht an"
description: Wenden Sie den Patch ACSD-54319 an, um das Adobe Commerce-Problem zu beheben, bei dem der Produktpreis im Bericht *[!UICONTROL Products in Carts]* null anzeigt.
feature: Reporting, Products
role: Admin, Developer
exl-id: f53b3ed3-d5d5-461c-bba2-4f9f3f038580
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# ACSD-54319: Produktpreis zeigt Null im Bericht *[!UICONTROL Products in Carts]* an

Der Patch ACSD-54319 behebt das Problem, dass der Produktpreis im Bericht *[!UICONTROL Products in Carts]* null anzeigt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 installiert ist. Die Patch-ID ist ACSD-54319. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.5-p5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Produktpreis zeigt im Bericht *[!UICONTROL Products in Carts]* null an.

<u>Zu reproduzierende Schritte</u>:

1. Setzen Sie **[!UICONTROL Catalog Price Scope]** von **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Price]** > **[!UICONTROL Catalog Price Scope]** auf **[!UICONTROL Website]**.
1. Erstellen Sie eine zweite Website von **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**.
1. Erstellen Sie ein Produkt aus **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Weisen Sie dieses Produkt nur der zweiten Website zu.
1. Fügen Sie auf der zweiten Website ein Produkt zum Warenkorb hinzu.
1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Reports]** > **[!UICONTROL Marketing]** > **[!UICONTROL Products In Carts]** Raster.
1. Überprüfen Sie die Spalte *[!UICONTROL Price]* im Raster *[!UICONTROL Products In Carts]*.

<u>Erwartete Ergebnisse</u>:

Der Produktpreis ist im Berichtraster *[!UICONTROL Products in Carts]* nicht null.

<u>Tatsächliche Ergebnisse</u>:

Der Produktpreis ist im Berichtraster *[!UICONTROL Products in Carts]* null.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
