---
title: 'Adobe Commerce 2.4.0 Bekanntes Problem: Amazon Bezahlen, keine Zahlungsmethoden'
description: Dieser Artikel bietet eine Lösung für ein bekanntes Problem in Adobe Commerce 2.4.0, bei dem Zahlungsmethoden fehlen, wenn Kundinnen und Kunden **Zur standardmäßigen Kasse zurückkehren** verwenden, nachdem sie Amazon Pay aktiviert haben.
exl-id: efd792c7-8970-4366-b9d1-4bf284ea96db
feature: B2B, Orders, Payments
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 Bekanntes Problem: Amazon Bezahlen, keine Zahlungsmethoden

Dieser Artikel bietet eine Lösung für ein bekanntes Problem in Adobe Commerce 2.4.0, bei dem Zahlungsmethoden fehlen, wenn Kundinnen und Kunden **Zur standardmäßigen Kasse zurückkehren** verwenden, nachdem sie Amazon Pay aktiviert haben.

## Betroffene Produkte und Versionen

Adobe Commerce On-Premises und Adobe Commerce on Cloud Infrastructure v2.3.5.p1 und v2.4.0

<u>Schritte zur Reproduktion:</u>

1. Navigieren Sie zur Storefront.
1. Fügen Sie einen beliebigen Artikel zum Warenkorb hinzu und fahren Sie mit der Kasse fort.
1. Melden Sie sich bei Ihrem Amazon Pay-Konto an.
1. Wählen Sie eine Adresse aus und fahren Sie mit der Kasse fort.
1. Klicken Sie **Zurück zur standardmäßigen**).
1. Fahren Sie mit der Kasse fort.

<u>Erwartete Ergebnisse:</u>

Zahlungsmethoden sollten nach dem Neustart des Checkouts angezeigt werden.

<u>Tatsächliche Ergebnisse:</u>

Zahlungsmethoden fehlen.

## Lösung

Für 2.4.1 ist eine Lösung geplant.

## Weiterführende Informationen finden Sie in unserer Support-Wissensdatenbank:

* [Bekanntes Problem mit Adobe Commerce 2.4.0: Fehlermeldung bei Auswahl der lokalen Zahlungsmethode, die für einige Länder während des Checkouts angezeigt wird](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: 404-Fehler beim Entfernen von Prämienpunkten beim Checkout für mehrere Sendungen](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Fehler bei der Anzeige von Bestellungen](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0 B2B-Admin kann kein konfigurierbares Produkt zum Angebot hinzufügen](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0 Bekanntes Problem: Braintree-Zahlungsmethoden werden beim Checkout für mehrere Adressen nicht angezeigt](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0 - Aktualisierung der Aktivitäten des Kunden funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 bekanntes Problem - Exportsteuersätze funktionieren nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Die Schaltfläche „Auswahl zu meinem Warenkorb hinzufügen“ funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Rohnachrichtendaten werden in der Storefront angezeigt](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
