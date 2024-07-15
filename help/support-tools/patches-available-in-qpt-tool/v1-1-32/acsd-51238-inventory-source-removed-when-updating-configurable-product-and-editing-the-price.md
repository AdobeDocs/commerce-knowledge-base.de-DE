---
title: "ACSD-51238: Inventarquelle wird beim Aktualisieren eines konfigurierbaren Produkts und Bearbeiten des Preises entfernt"
description: Wenden Sie den Patch ACSD-51238 an, um das Adobe Commerce-Problem zu beheben, bei dem die Inventarquelle beim Aktualisieren eines konfigurierbaren Produkts und Bearbeiten des Preises entfernt wird.
exl-id: ab2f60fd-5da3-45f7-a489-6f4f9d34e1f1
feature: Configuration, Inventory, Orders, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-51238: Die Inventarquelle wird beim Aktualisieren eines konfigurierbaren Produkts und Bearbeiten des Preises entfernt

Der Patch ACSD-51238 behebt das Problem, dass die Inventarquelle beim Aktualisieren eines konfigurierbaren Produkts und Bearbeiten des Preises entfernt wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.32 installiert ist. Die Patch-ID ist ACSD-51238. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Inventarquelle wird beim Aktualisieren eines konfigurierbaren Produkts und Bearbeiten des Preises entfernt.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie **[!DNL Adobe Commerce]** mit **[!DNL Inventory module]**
1. Gehen Sie zu &quot;**[!UICONTROL Admin]** -> **[!UICONTROL Stores]** -> **[!UICONTROL Inventory]**&quot;und erstellen Sie *zwei Quellen* und *zwei Lager*.
1. Erstellen Sie eine **[!UICONTROL configurable product]** und weisen Sie sie **[!UICONTROL default sources]** oder **[!UICONTROL newly created sources]** zu.
1. Klicken Sie auf die Werte **[!UICONTROL next button]** und *save* für das Produkt.
1. Bearbeiten Sie nun denselben **[!UICONTROL Configurable Product]** und klicken Sie auf **[!UICONTROL Edit Configuration]** innerhalb des **[!UICONTROL Configuration tab]**.
1. Ändern Sie in `Step 3: Bulk Images,Price and Quantity` die `price` und lassen Sie `Quantity` und `Images` auf `Skip quantity at this time` bzw. `Skip image uploading at this time`.
1. Klicken Sie auf **[!UICONTROL next button]** und generieren Sie das Produkt.

<u>Erwartete Ergebnisse</u>

Die Menge pro Quelle innerhalb der **[!UICONTROL Configuration tab]** sollte nicht leer sein.

<u>Tatsächliche Ergebnisse</u>

Die Menge pro Quelle innerhalb der **[!UICONTROL Configuration tab]** ist leer.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) im [!DNL Quality Patches Tool] -Handbuch.
