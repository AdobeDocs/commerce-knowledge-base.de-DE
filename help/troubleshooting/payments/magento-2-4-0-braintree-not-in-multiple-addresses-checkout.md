---
title: 'Adobe Commerce 2.4.0: Braintree nicht im Checkout für mehrere Adressen'
description: Dieser Artikel bietet eine Problemumgehung für ein bekanntes Adobe Commerce 2.4.0-Problem, bei dem Braintree-Zahlungsmethoden nicht in die Arbeit mit dem Checkout für mehrere Adressen einbezogen sind. Beachten Sie, dass das Problem in Adobe Commerce 2.4.1 behoben wurde.
exl-id: efde0bba-fd4a-490b-becb-856cb9ea58a5
feature: Checkout, Compliance, Orders, Payments, Shipping/Delivery
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: Braintree nicht im Checkout für mehrere Adressen

Dieser Artikel bietet eine Problemumgehung für ein bekanntes Adobe Commerce 2.4.0-Problem, bei dem Braintree-Zahlungsmethoden nicht in die Arbeit mit dem Checkout für mehrere Adressen einbezogen sind. Beachten Sie, dass das Problem in Adobe Commerce 2.4.1 behoben wurde.

Hinweis: Adobe Commerce empfiehlt die Verwendung der [Commerce Marketplace-Braintree-Erweiterung](https://marketplace.magento.com/paypal-module-braintree.html) für Version 2.3 und höher, um die PSD-Konformität zu wahren. Die Erweiterung bietet nicht die Funktion zum Auschecken über mehrere Adressen.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premise v2.4.0
* Adobe Commerce auf Cloud-Infrastruktur v2.4.0

## Problem

<u>Voraussetzungen</u>:

Die Core Braintree-Integration wird verwendet.

<u>Schritte zur Reproduktion</u>:

1. Geh zum Laden.
1. Melden Sie sich als Kunde an.
1. Fügen Sie ein Produkt zum Warenkorb hinzu.
1. Öffnen Sie den Warenkorb.
1. Drücken Sie **Warenkorb anzeigen und bearbeiten**.
1. Drücken Sie **Mit mehreren Adressen auschecken**.
1. Drücken Sie **Zu Versandinformationen gehen**.
1. Drücken Sie **Weiter zu Rechnungsinformationen**.

<u>Erwartetes Ergebnis</u>:

Braintree ist als Zahlungsmethode verfügbar.

<u>Tatsächliches </u>:

Braintree ist nicht als Zahlungsmethode verfügbar.

## Abhilfe

Aktivieren Sie keine Optionen für mehrere Adressen, wenn Sie Braintree in Adobe Commerce 2.4.0 verwenden. Dieses Problem wurde in Adobe Commerce 2.4.1 behoben.

## Lesen Sie diesbezüglich in unserer Support-Wissensdatenbank

* [Bekanntes Problem in Adobe Commerce 2.4.0 - Aktualisierung der Aktivitäten des Kunden funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Rohnachrichtendaten werden in der Storefront angezeigt](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0 bekanntes Problem - Exportsteuersätze funktionieren nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Die Schaltfläche „Auswahl zu meinem Warenkorb hinzufügen“ funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
