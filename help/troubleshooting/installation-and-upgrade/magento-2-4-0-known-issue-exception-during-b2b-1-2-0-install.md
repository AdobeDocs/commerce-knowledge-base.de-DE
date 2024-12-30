---
title: 'Adobe Commerce 2.4.0: Ausnahme während der B2B 1.2.0-Installation'
description: Dieser Artikel enthält eine Fehlerbehebung für ein bekanntes Problem in Adobe Commerce bei einer Ausnahme, die während „setup:upgrade“ bei der Installation von B2B 1.2.0 ausgelöst wurde.
exl-id: 2c1dadd9-7754-4b4c-8d37-b75c13beae5c
feature: B2B, Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: Ausnahme während der B2B 1.2.0-Installation

Dieser Artikel enthält eine Fehlerbehebung für ein bekanntes Problem in Adobe Commerce für eine Ausnahme, die während der `setup:upgrade` bei der Installation von B2B 1.2.0 ausgelöst wurde.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises 2.4.0
* Adobe Commerce auf Cloud-Infrastruktur 2.4.0
* B2B 1.2.0

## Problem

<u>Schritte zur Reproduktion</u>

1. Installieren Sie Adobe Commerce, wobei mehr als ein Store erstellt wurde.
1. Erstellen Sie einen zusätzlichen Store.
1. Installieren Sie B2B 1.2.0.

>[!WARNING]
>
>Das Upgrade jeder B2B-Instanz mit mehr als einem Store aus einer Version unter 1.2.0 oder einer Commerce-Instanz unter 2.4.0 ist ebenfalls betroffen.

<u>Erwartetes Ergebnis</u>

B2B 1.2.0-Installationen.

<u>Tatsächliches Ergebnis</u>

Wenn `setup:upgrade` die Installation von B2B 1.2.0 durchführt, wird dieser Fehler im `PurchaseOrder`-Modul angezeigt:

```php
Module 'Magento_PurchaseOrder':
  Unable to apply data patch Magento\PurchaseOrder\Setup\Patch\Data\InitPurchaseOrderSalesSequence
  for module Magento_PurchaseOrder. Original exception message: DDL statements
  are not allowed in transactions
```

## Lösung

Wenden Sie das in diesem Artikel vorgesehene Patch an.

## Fleck

Der Patch ist diesem Artikel beigefügt, der sowohl im `.composer`- als auch im `.git`-Format (nach dem Entpacken der Dateien) zum Download verfügbar ist.

Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf einen der folgenden Links:

* [Composer-Patch B2B-716\_composer.patch](assets/B2B-716_composer.patch.zip)
* [Git-Patch B2B-716\_git.patch](assets/B2B-716_git.patch.zip)

## Anwenden eines Pflasters

<u>Composer Patch-</u>

Anleitungen [ Composer-Patches finden Sie unter „Anwenden eines Composer-Patches ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) Adobe&quot;.

<u>Git-Patch-</u>

* Siehe [Anwenden von ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)&quot; in der Entwicklerdokumentation für Git-Patch-Anweisungen für Adobe Commerce in der Cloud-Infrastruktur.
* Siehe [Anwenden von Patches: Benutzerdefinierte Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview#custom-patches) in der Entwicklerdokumentation für Git-Patch-Anweisungen für Adobe Commerce.

## Verwandtes Lesen

* [Bekanntes Problem in Adobe Commerce 2.4.0: Rohnachrichtendaten werden in der Storefront angezeigt](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0 Bekanntes Problem: Exportsteuersätze funktionieren nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 Bekanntes Problem: Braintree-Zahlungsmethoden werden beim Checkout für mehrere Adressen nicht angezeigt](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Fehlermeldung bei Auswahl der lokalen Zahlungsmethode, die für einige Länder während des Checkouts angezeigt wird](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: 404-Fehler beim Entfernen von Prämienpunkten beim Checkout für mehrere Sendungen](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Fehler bei der Anzeige von Bestellungen](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0 B2B-Admin kann kein konfigurierbares Produkt zum Angebot hinzufügen](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0 - Aktualisierung der Aktivitäten des Kunden funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Die Schaltfläche „Auswahl zu meinem Warenkorb hinzufügen“ funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
