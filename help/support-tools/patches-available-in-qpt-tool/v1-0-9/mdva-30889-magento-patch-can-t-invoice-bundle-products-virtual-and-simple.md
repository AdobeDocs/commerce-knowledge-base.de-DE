---
title: "MDVA-30889: Kann Bundle-Produkte nicht virtuell und einfach berechnen"
description: Der Patch MDVA-30889 behebt das Problem, bei dem nach der Fakturierung eines Bundle-Produkts mit virtuellen und einfachen Optionen ein Fehler auftritt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.
exl-id: 7e6555c5-9088-4c85-920d-20c841ad6675
feature: Invoices, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-30889: Gebündelte Produkte nicht virtuell und einfach berechnen

Der Patch MDVA-30889 behebt das Problem, bei dem nach der Fakturierung eines Bundle-Produkts mit virtuellen und einfachen Optionen ein Fehler auftritt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Voraussetzungen</u>:

Installieren Sie Adobe Commerce mit [Inventory management](https://devdocs.magento.com/guides/v2.4/inventory/).

<u>Zu reproduzierende Schritte</u>:

1. Wechseln Sie zu **Admin**.
1. Erstellen Sie ein einfaches Produkt.
1. Erstellen eines virtuellen Produkts.
1. Erstellen Sie ein Bundle-Produkt (Erstellen Sie zwei Dropdown-Optionen für untergeordnete Produkte und weisen Sie virtuelle und einfache Produkte zu.) Legen Sie **Dynamischer Preis** = *Nein* fest.
1. Gehen Sie zur Storefront.
1. Rufen Sie die Seite des Produkts auf.
1. Fügen Sie das Produkt zum Warenkorb hinzu.
1. Fahren Sie mit dem Checkout fort und bestellen Sie das Produkt.
1. Navigieren Sie zu **Admin > Bestellungen**.
1. Öffnen Sie die erstellte Bestellung und rechnen Sie sie in Rechnung.

<u>Erwartete Ergebnisse</u>:

Die Rechnung eines Bundle-Produkts (das sowohl einfache als auch virtuelle Produkte enthält) wird erstellt.

<u>Tatsächliche Ergebnisse</u>:

Die Rechnung wird nicht erstellt und Sie erhalten einen Fehler wie den folgenden:

```php
TypeError: Return value of Magento\InventorySourceSelection\Model\Request\InventoryRequest::getItems() must be of the type array, null returned in vendor/magento/module-inventory-source-selection/Model/Request/InventoryRequest.php:102
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
