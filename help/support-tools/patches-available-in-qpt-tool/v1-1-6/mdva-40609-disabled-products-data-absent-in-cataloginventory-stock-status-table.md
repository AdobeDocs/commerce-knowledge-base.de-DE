---
title: 'MDVA-40609: Deaktivierte Produktdaten fehlen in der Tabelle catalogInventory_stock_status'
description: Der MDVA-40609 Patch löst das Problem, dass die deaktivierten Produktdaten nicht in der Indextabelle „cataloginventory_stock_status“ angezeigt werden, was dazu führt, dass falsche Produktmengen angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-40609. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
exl-id: 2424c3b3-8bc9-4dd4-908c-9d653f09a57a
feature: Catalog Management, Inventory, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-40609: Deaktivierte Produktdaten fehlen in der Tabelle catalogInventory_stock_status

Der MDVA-40609 Patch löst das Problem, dass die Daten für deaktivierte Produkte nicht in der `cataloginventory_stock_status` angezeigt werden, was dazu führt, dass falsche Produktmengen angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-40609. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Deaktivierte Produktdaten werden nicht in der `cataloginventory_stock_status` angezeigt, was zur Anzeige falscher Produktmengen führt.

<u>Voraussetzungen</u>:

Das Inventar-Modul ist installiert.

<u>Schritte zur Reproduktion</u>:

1. Richten Sie zwei Websites mit Stores und Store-Ansichten ein.
1. Erstellen Sie eine zusätzliche Quelle und einen zusätzlichen Lagerbestand.
1. Einfaches Produkt hinzufügen:
   * Aktivieren Sie Produkt auf *Nein*.
   * Weisen Sie zwei Bezugsquellen mit Source Artikelstatus = Lagerbestand und einer Menge größer als Null zu.
1. Speichern Sie das Produkt.
1. Überprüfen Sie die **Produktverkaufsmenge**.

<u>Erwartete Ergebnisse</u>:

Beide Bestände haben Werte von mehr als null eingegeben.

<u>Tatsächliche Ergebnisse</u>:

Eine Aktie hat einen Nullwert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
