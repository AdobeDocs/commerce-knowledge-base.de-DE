---
title: "Adobe Commerce 2.4.0: Braintree not in Multiple Addresses Checkout"
description: Dieser Artikel bietet eine Problemumgehung für ein bekanntes Adobe Commerce 2.4.0-Problem, bei dem Braintree-Zahlungsmethoden nicht beim Arbeiten mit dem Checkout für mehrere Adressen enthalten sind. Beachten Sie, dass das Problem in Adobe Commerce 2.4.1 behoben wurde.
exl-id: efde0bba-fd4a-490b-becb-856cb9ea58a5
feature: Checkout, Compliance, Orders, Payments, Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: Braintree nicht an mehreren Adressen checkout

Dieser Artikel bietet eine Problemumgehung für ein bekanntes Adobe Commerce 2.4.0-Problem, bei dem Braintree-Zahlungsmethoden nicht beim Arbeiten mit dem Checkout für mehrere Adressen enthalten sind. Beachten Sie, dass das Problem in Adobe Commerce 2.4.1 behoben wurde.

Hinweis: Adobe Commerce empfiehlt die Verwendung der [Commerce Marketplace-Braintree-Erweiterung](https://marketplace.magento.com/paypal-module-braintree.html) für Versionen 2.3 und höher, um die PSD-Konformität zu wahren. Die Erweiterung bietet keine Funktion zum Auschecken mehrerer Adressen.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premise v2.4.0
* Adobe Commerce auf Cloud-Infrastruktur v2.4.0

## Problem

<u>Voraussetzungen</u>:

Die Core-Braintree-Integration wird verwendet.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zur Storefront.
1. Melden Sie sich als Kunde an.
1. Fügen Sie dem Warenkorb ein Produkt hinzu.
1. Öffnen Sie Ihren Warenkorb.
1. Drücken Sie **Warenkorb anzeigen und bearbeiten**.
1. Drücken Sie **Mit mehreren Adressen auschecken**.
1. Drücken Sie die Taste **Gehe zu Versandinformationen**.
1. Drücken Sie **Weiter zu Rechnungsinformationen**.

<u>Erwartetes Ergebnis</u>:

Braintree ist als Zahlungsmethode erhältlich.

<u>Tatsächliches Ergebnis</u>:

Braintree ist nicht als Zahlungsmethode verfügbar.

## Workaround

Aktivieren Sie bei Verwendung von Braintree in Adobe Commerce 2.4.0 keine Optionen für mehrere Adressen. Dieses Problem wurde in Adobe Commerce 2.4.1 behoben.

## Verwandtes Lesen in unserer Wissensdatenbank

* [Bekanntes Problem mit Adobe Commerce 2.4.0 - Aktualisierung der Kundenaktivitäten funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Bekanntes Problem bei der Erstellung von Versandbeschriftungen in Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Rohdaten werden in Storefront angezeigt](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0 - Exportsteuersätze funktionieren nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Schaltfläche &quot;Auswahl zum Warenkorb hinzufügen&quot;funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
