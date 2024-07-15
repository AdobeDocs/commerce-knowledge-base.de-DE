---
title: Die Installation von Adobe Commerce 2.4.0 schlägt mit veraltetem Speicher-Cache fehl
description: "Dieser Artikel bietet eine Lösung für das Problem, bei dem Ihre Adobe Commerce 2.4.0-Installation mit der Fehlermeldung fehlschlägt: *Die Standardwebsite ist nicht definiert. Legen Sie die Website fest und versuchen Sie es erneut.* in der Konsole angezeigt."
exl-id: 0680199b-7e47-4a8c-91fe-9f6c32839a0e
feature: B2B, Cache, Console, Install, Upgrade
role: Developer
source-git-commit: 2bba3af8919e1db8482764b8d688f95e606c2683
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# Die Installation von Adobe Commerce 2.4.0 schlägt mit veraltetem Speicher-Cache fehl

Dieser Artikel bietet eine Lösung für das Problem, bei dem Ihre Adobe Commerce 2.4.0-Installation mit der Fehlermeldung fehlschlägt: *Die Standardwebsite ist nicht definiert. Legen Sie die Website fest und versuchen Sie es erneut.* in der Konsole angezeigt.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.4.0
* Adobe Commerce vor Ort 2.4.0

## Problem

<u>Voraussetzungen:</u>
Eine Drittanbietererweiterung mit Abhängigkeiten von APIs für das Store-Modul in CLI-Befehlen wird wie in `composer.json` erforderlich konfiguriert. Dies führt dazu, dass die Installation von Adobe Commerce 2.4.0 mit einer Fehlermeldung fehlschlägt: *Die Standardwebsite ist nicht definiert. Legen Sie die Website fest und versuchen Sie es erneut.* in der Konsole angezeigt.

## Ursache

Das Problem wird für die Drittanbietererweiterungen angezeigt, die in ihren CLI-Befehlen von Stores abhängig sind. Einer davon sind Amazon-Sales Channel.

## Lösung

Vor der Installation von Adobe Commerce 2.4.0 müssen Händler:

1. Entfernen Sie diese Drittanbietererweiterungen aus `composer.json`.
1. Installieren Sie Adobe Commerce ohne Erweiterungen.
1. Fügen Sie die Erweiterungen nach der Installation hinzu.

Das Problem wird in Version 2.4.1 behoben.

## Verwandte Lesungen in unserer Wissensdatenbank:

* [Bekanntes Problem bei Adobe Commerce 2.4.0: fehlendes &quot;Refund&quot;-Label in Klarna](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Zwei Schaltflächen fehlen auf der Seite &quot;Neue Bestellung erstellen&quot;in Admin](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-create-new-order-buttons-missing.md)
* [Adobe Commerce 2.4.0, 2.4.1: Braintree Venmo-Teilrechnungsproblem aktivieren](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Fehlermeldung bei Auswahl der lokalen Zahlungsmethode, die für einige Länder beim Checkout angezeigt wird](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Amazon-Pay-fähig, Zahlungsmethoden fehlen bei Rückkehr zum Standard-Checkout, verwendet](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: 404-Fehler beim Entfernen von Belohnungspunkten beim Checkout mit mehreren Sendungen](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Bestellungen zeigen Fehler an](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0 B2B Admin kann kein konfigurierbares Produkt zum Anführungszeichen hinzufügen](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Braintree-Zahlungsmethoden werden beim Checkout für mehrere Adressen nicht angezeigt](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Bekanntes Problem bei der Erstellung von Versandbeschriftungen in Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0 - Aktualisierung der Kundenaktivitäten funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0 - Exportsteuersätze funktionieren nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Schaltfläche &quot;Auswahl zum Warenkorb hinzufügen&quot;funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Rohdaten werden in Storefront angezeigt](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
