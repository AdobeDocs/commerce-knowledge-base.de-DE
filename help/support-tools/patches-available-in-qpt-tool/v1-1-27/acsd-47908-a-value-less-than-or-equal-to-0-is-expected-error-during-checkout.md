---
title: 'ACSD-47908: *Ein Wert kleiner oder gleich 0 wird erwartet* Fehler beim Checkout'
description: Wenden Sie den Patch ACSD-47908 an, um den Adobe Commerce-Fehler zu beheben *Ein Wert kleiner oder gleich 0 wird erwartet* bei der Auswahl der Quelle und Menge im Versandschritt während des Checkouts.
exl-id: fec90e4b-9cb8-4cd9-9e85-ccada840c896
feature: Admin Workspace, Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# ACSD-47908: *Ein Wert kleiner oder gleich 0 wird beim Checkout erwartet* Fehler.

Der Patch ACSD-47908 behebt den Fehler *Ein Wert kleiner oder gleich 0 wird erwartet* bei der Auswahl der Quelle und Menge im Versandschritt beim Checkout. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 installiert ist. Die Patch-ID ist ACSD-47908. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der folgende Fehler wird bei der Auswahl der Quelle und Menge im Versandschritt beim Checkout ausgegeben: *Ein Wert kleiner oder gleich 0 wird erwartet*.

<u>Voraussetzungen</u>:

Installieren Sie die Adobe Commerce Inventory management (MSI)-Module.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Sources]** und konfigurieren Sie mehrere Quellen.
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]** und erstellen Sie einen neuen Bestand.
   * Weisen Sie nun die Quellen dem neuen Lager zu.
1. Gehen Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** und bearbeiten Sie mindestens ein Produkt.
   * Stellen Sie sicher, dass die Produkte den neuen Quellen zugewiesen sind, und geben Sie die verfügbare Menge an.
1. Gehen Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Orders]** und erstellen Sie eine neue Bestellung.
1. Fügen Sie diese Produkte der Bestellung hinzu und platzieren Sie sie.
1. Klicken Sie auf **[!UICONTROL Ship]**.
1. Wählen Sie die Quelle aus, aus der der Versand durchgeführt werden soll.
1. Geben Sie die Menge jedes zu versendenden Artikels an.
1. Laden Sie die Seite neu.
1. Klicken Sie auf **[!UICONTROL Proceed to Shipment]**.

<u>Erwartete Ergebnisse</u>:

Die neue Versandseite wird ohne Fehler geöffnet.

<u>Tatsächliche Ergebnisse</u>:

* Die eingegebene Menge kann nicht validiert werden.
* Der folgende Fehler wird ausgegeben: *Geben Sie einen Wert ein, der kleiner oder gleich 0* ist.

  Der Fehler ist jedoch inkonsistent und erscheint möglicherweise nicht immer.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
