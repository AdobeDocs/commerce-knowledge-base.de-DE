---
title: "Adobe Commerce 2.4.0: Ausnahme während B2B 1.2.0-Installation"
description: Dieser Artikel enthält eine Fehlerbehebung für ein bekanntes Adobe Commerce-Problem, das bei der Installation von B2B 1.2.0 für eine Ausnahme ausgelöst wurde, die während "setup:upgrade"ausgelöst wurde.
exl-id: 2c1dadd9-7754-4b4c-8d37-b75c13beae5c
feature: B2B, Install, Upgrade
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: Ausnahme während B2B 1.2.0-Installation

Dieser Artikel enthält eine Fehlerbehebung für ein bekanntes Adobe Commerce-Problem, bei dem bei der Installation von B2B 1.2.0 eine Ausnahme ausgelöst wurde, die während `setup:upgrade` ausgelöst wurde.

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort 2.4.0
* Adobe Commerce auf Cloud-Infrastruktur 2.4.0
* B2B 1.2.0

## Problem

<u>Zu reproduzierende Schritte</u>

1. Installieren Sie Adobe Commerce mit mehreren erstellten Stores.
1. Erstellen Sie einen zusätzlichen Store.
1. Installieren Sie B2B 1.2.0.

>[!WARNING]
>
>Das Upgrade einer B2B-Instanz mit mehr als 1 Store von einer Version unter 1.2.0 oder einer Commerce-Instanz unter 2.4.0 ist ebenfalls betroffen.

<u>Erwartetes Ergebnis</u>

B2B 1.2.0 wird installiert.

<u>Tatsächliches Ergebnis</u>

Wenn `setup:upgrade` zur Installation von B2B 1.2.0 ausgeführt wird, wird dieser Fehler im `PurchaseOrder`-Modul angezeigt:

```php
Module 'Magento_PurchaseOrder':
  Unable to apply data patch Magento\PurchaseOrder\Setup\Patch\Data\InitPurchaseOrderSalesSequence
  for module Magento_PurchaseOrder. Original exception message: DDL statements
  are not allowed in transactions
```

## Lösung

Wenden Sie den in diesem Artikel bereitgestellten Patch an.

## Patch

Der Patch ist an diesen Artikel angehängt, der sowohl im `.composer`- als auch im `.git` -Format zum Download bereitsteht (nachdem Sie die Dateien entpackt haben).

Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf einen der folgenden Links:

* [Composer Patch B2B-716\_Composer.patch](assets/B2B-716_composer.patch.zip)
* [Git Patch B2B-716\_git.patch](assets/B2B-716_git.patch.zip)

## Anwenden eines Pflasters

<u>Composer-Patch </u>

Informationen zum Patchanweisungen für Composer finden Sie unter [Anwenden eines von Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches.

<u>Git Patch </u>

* Informationen zu Git-Patch-Anweisungen für Adobe Commerce in der Cloud-Infrastruktur finden Sie unter [Anwenden von Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in der Entwicklerdokumentation.
* Informationen zu Git-Patch-Anweisungen für Adobe Commerce finden Sie unter [Anwenden von Patches: Benutzerdefinierte Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#custom-patches) in der Entwicklerdokumentation.

## Verwandtes Lesen

* [Bekanntes Problem mit Adobe Commerce 2.4.0: Rohdaten werden in Storefront angezeigt](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Exportsteuersätze funktionieren nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Braintree-Zahlungsmethoden werden beim Checkout für mehrere Adressen nicht angezeigt](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Fehlermeldung bei Auswahl der lokalen Zahlungsmethode, die für einige Länder beim Checkout angezeigt wird](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: 404-Fehler beim Entfernen von Belohnungspunkten beim Checkout mit mehreren Sendungen](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Bestellungen zeigen Fehler an](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0 B2B Admin kann kein konfigurierbares Produkt zum Anführungszeichen hinzufügen](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0 - Aktualisierung der Kundenaktivitäten funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Schaltfläche &quot;Auswahl zum Warenkorb hinzufügen&quot;funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
