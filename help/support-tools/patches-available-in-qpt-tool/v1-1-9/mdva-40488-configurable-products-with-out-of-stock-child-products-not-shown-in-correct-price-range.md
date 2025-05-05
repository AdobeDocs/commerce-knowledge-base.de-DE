---
title: 'MDVA-40488: Konfigurierbare Produkte mit nicht vorrätigen untergeordneten Produkten werden nicht in der richtigen Preisspanne angezeigt'
description: Der MDVA-40488 Patch löst das Problem, dass konfigurierbare Produkte mit nicht vorrätigen untergeordneten Produkten nicht in der richtigen Preisklasse angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-40488. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
exl-id: 0c4b9f5e-ae41-409e-b244-1d7cf948ed6f
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---

# MDVA-40488: Konfigurierbare Produkte mit nicht vorrätigen untergeordneten Produkten werden nicht in der richtigen Preisspanne angezeigt

Der MDVA-40488 Patch löst das Problem, dass konfigurierbare Produkte mit nicht vorrätigen untergeordneten Produkten nicht in der richtigen Preisklasse angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-40488. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Konfigurierbare Produkte mit nicht vorrätigen untergeordneten Produkten werden nicht in der richtigen Preisspanne angezeigt.

<u>Voraussetzungen</u>:

Wechseln Sie zur Konfiguration Commerce Admin > **Stores** > **configuration** > **catalog** > **Inventory** > **Stock-Optionen** und **Display Out of Stock Products** auf *Yes*.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein konfigurierbares Produkt mit zwei zugehörigen Produkten. Zum Beispiel: einfache Produkte Rot und Braun.
1. Setzen Sie den Bestand des einfachen Produkts auf Rot, und setzen Sie den Lagerstatus auf *Auf Lager*, und setzen Sie dann den Produktstatus aktivieren auf *Nein*.
1. Legen Sie den Bestand des einfachen braunen Produkts fest und setzen Sie dann den Produktstatus aktivieren auf *Ja*.
1. Stellen Sie sicher, dass der konfigurierbare Produktlagerstatus &quot;*&quot;*.
1. Ändern Sie den Bestand des einfachen braunen Produkts auf 0 und setzen Sie den Lagerstatus auf *Nicht vorrätig*.
1. Zu diesem Zeitpunkt ist der konfigurierbare Produktbestandsstatus noch &quot;*&quot;*.
1. Neuindizierung durchführen.
1. Überprüfen Sie die `min_price` und `max_price` für das konfigurierbare Produkt in der `catalog_product_index_price` DB-Tabelle. Die beiden Werte sind auf 0 gesetzt.
1. Wenn wir jedoch den Lagerstatus des konfigurierbaren Produkts auf *Nicht vorrätig* setzen und eine Neuindizierung durchführen, können wir `min_price` und `max_price` Werte ungleich null des konfigurierbaren Produkts sehen.

<u>Erwartete Ergebnisse</u>:

Wenn alle untergeordneten Produkte *nicht vorrätig* und das konfigurierbare Produkt selbst ebenfalls *nicht vorrätig* ist, wird der Preis anhand aller untergeordneten Produkte berechnet.

<u>Tatsächliche Ergebnisse</u>:

Die `min_price`- und `max_price` für das konfigurierbare Produkt in der `catalog_product_index_price` DB-Tabelle werden auf 0 gesetzt, wenn der konfigurierbare Lagerstatus „Auf Lager *ist*, aber wenn er *Nicht vorrätig* ist, werden sie zu Werten ungleich null.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
