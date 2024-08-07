---
title: "MDVA-40488: Konfigurierbare Produkte mit nicht vorrätigen untergeordneten Produkten, die nicht in der richtigen Preisspanne angezeigt werden"
description: Der Patch MDVA-40488 behebt das Problem, dass konfigurierbare Produkte mit nicht vorrätigen untergeordneten Produkten nicht in ihrer korrekten Preisspanne angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-40488. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: 0c4b9f5e-ae41-409e-b244-1d7cf948ed6f
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---

# MDVA-40488: Konfigurierbare Produkte mit nicht vorrätigen untergeordneten Produkten werden nicht in der richtigen Preisspanne angezeigt

Der Patch MDVA-40488 behebt das Problem, dass konfigurierbare Produkte mit nicht vorrätigen untergeordneten Produkten nicht in ihrer korrekten Preisspanne angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-40488. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Konfigurierbare Produkte mit nicht vorrätigen untergeordneten Produkten werden nicht in der korrekten Preisspanne angezeigt.

<u>Voraussetzungen</u>:

Gehen Sie zu Commerce Admin > **stores** > **configuration** > **catalog** > **Inventory** > **stock options** und stellen Sie die Konfiguration **Nicht vorrätige Produkte anzeigen** auf *Ja* ein.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein konfigurierbares Produkt mit zwei zugehörigen Produkten. Beispiel: einfache Produkte Rot und Braun.
1. Legen Sie den Bestand des einfachen Produkts Rot fest, legen Sie den Lagerstatus auf *Auf Lager* fest und setzen Sie dann den Status Produkt aktivieren auf *Nein*.
1. Legen Sie den Bestand des einfachen Produkts Braun fest und setzen Sie dann den Status Produkt aktivieren auf *Ja*.
1. Stellen Sie sicher, dass der konfigurierbare Produktspeicherstatus *Auf Lager* ist.
1. Ändern Sie den Lagerbestand des einfachen Produkts braun auf 0 und legen Sie den Lagerstatus auf *Nicht auf Lager* fest.
1. An dieser Stelle ist der konfigurierbare Produktspeicherstatus immer noch *Auf Lager*.
1. Führen Sie eine Neuindizierung durch.
1. Überprüfen Sie die `min_price` und `max_price` für das konfigurierbare Produkt in der `catalog_product_index_price` DB-Tabelle. Die beiden Werte sind auf 0 gesetzt.
1. Wenn wir jedoch den konfigurierbaren Produktstatus auf *Nicht vorrätig* setzen und eine Neuindizierung vornehmen, können wir die Werte ungleich null `min_price` und `max_price` des konfigurierbaren Produkts sehen.

<u>Erwartete Ergebnisse</u>:

Wenn alle untergeordneten Produkte *nicht auf Lager* sind und das konfigurierbare Produkt selbst ebenfalls *nicht auf Lager ist*, wird der Preis anhand aller untergeordneten Produkte berechnet.

<u>Tatsächliche Ergebnisse</u>:

Die Werte `min_price` und `max_price` für das konfigurierbare Produkt in der `catalog_product_index_price` DB-Tabelle werden auf 0 gesetzt, wenn der konfigurierbare Bestandsstatus *Auf Lager* ist, aber wenn es *Nicht auf Lager* ist, werden sie zu Werten ungleich null.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
