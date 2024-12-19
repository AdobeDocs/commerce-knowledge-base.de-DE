---
title: 'ACSD-47908: *Beim Auschecken wird ein Wert kleiner oder gleich 0 erwartet* Fehler'
description: Wenden Sie den Patch ACSD-47908 an, um den Adobe Commerce-Fehler zu beheben. *Es wird ein Wert kleiner oder gleich 0 erwartet, wenn Sie während des Checkouts die Quelle und Menge im Versandschritt auswählen.
exl-id: fec90e4b-9cb8-4cd9-9e85-ccada840c896
feature: Admin Workspace, Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# ACSD-47908: *Es wird ein Wert kleiner oder gleich 0 erwartet* Fehler beim Auschecken

Der Patch ACSD-47908 behebt den Fehler *Ein Wert kleiner oder gleich 0 wird erwartet* wenn die Quelle und Menge im Versandschritt während des Checkouts ausgewählt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 installiert ist. Die Patch-ID ist ACSD-47908. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Bei der Auswahl der Quelle und Menge im Versandschritt während des Checkouts wird folgender Fehler ausgelöst: *Es wird ein Wert kleiner oder gleich 0 erwartet*.

<u>Voraussetzungen</u>:

Installieren Sie Adobe Commerce Inventory management (MSI)-Module.

<u>Schritte zur Reproduktion</u>:

1. Wechseln Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Sources]** und konfigurieren Sie mehrere Quellen.
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]** und erstellen Sie ein neues Lager.
   * Weisen Sie nun die Quellen dem neuen Lager zu.
1. Gehen Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** und bearbeiten Sie mindestens ein Produkt.
   * Stellen Sie sicher, dass die Produkte den neuen Quellen zugewiesen sind, und geben Sie die verfügbare Menge an.
1. Gehen Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Orders]** und erstellen Sie eine neue Bestellung.
1. Fügen Sie diese Produkte zur Bestellung hinzu und platzieren Sie sie.
1. Klicken Sie auf **[!UICONTROL Ship]**.
1. Quelle auswählen, von der aus geliefert werden soll.
1. Geben Sie die Menge jedes zu versendenden Artikels an.
1. Laden Sie die Seite neu.
1. Klicken Sie auf **[!UICONTROL Proceed to Shipment]**.

<u>Erwartete Ergebnisse</u>:

Die neue Sendungsseite wird ohne Fehler geöffnet.

<u>Tatsächliche Ergebnisse</u>:

* Die eingegebene Menge kann nicht validiert werden.
* Folgender Fehler wird ausgegeben: *Bitte einen Wert kleiner oder gleich 0 eingeben*.

  Der Fehler ist jedoch inkonsistent und tritt möglicherweise nicht immer auf.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
