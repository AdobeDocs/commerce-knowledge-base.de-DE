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

Der Patch ACSD-51238 behebt das Problem, dass die Inventarquelle beim Aktualisieren eines konfigurierbaren Produkts und Bearbeiten des Preises entfernt wird. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.32 installiert ist. Die Patch-ID ist ACSD-51238. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Inventarquelle wird beim Aktualisieren eines konfigurierbaren Produkts und Bearbeiten des Preises entfernt.

<u>Zu reproduzierende Schritte</u>:

1. Installieren **[!DNL Adobe Commerce]** mit **[!DNL Inventory module]**
1. Navigieren Sie zu **[!UICONTROL Admin]** -> **[!UICONTROL Stores]** -> **[!UICONTROL Inventory]** und erstellen *zwei Quellen* und *zwei Bestände*.
1. Erstellen Sie eine **[!UICONTROL configurable product]** und weisen Sie ihn zu **[!UICONTROL default sources]** oder **[!UICONTROL newly created sources]**.
1. Klicken Sie auf **[!UICONTROL next button]** und *save* das Produkt.
1. Bearbeiten Sie jetzt dasselbe **[!UICONTROL Configurable Product]** und auf **[!UICONTROL Edit Configuration]** innerhalb der **[!UICONTROL Configuration tab]**.
1. In `Step 3: Bulk Images,Price and Quantity`, ändern Sie die `price` und verlassen `Quantity` und `Images` nach `Skip quantity at this time` und `Skip image uploading at this time` bzw.
1. Klicken Sie auf **[!UICONTROL next button]** und generieren Sie das Produkt.

<u>Erwartete Ergebnisse</u>

Die Menge pro Quelle innerhalb der **[!UICONTROL Configuration tab]** sollte nicht leer sein.

<u>Tatsächliche Ergebnisse</u>

Die Menge pro Quelle innerhalb der **[!UICONTROL Configuration tab]** leer ist.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) im [!DNL Quality Patches Tool] Handbuch.
