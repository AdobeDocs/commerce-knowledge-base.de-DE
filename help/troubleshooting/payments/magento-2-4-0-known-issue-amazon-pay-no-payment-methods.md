---
title: "Bekanntes Adobe Commerce 2.4.0-Problem: Amazon-Zahlungsmittel, keine Zahlungsmethoden"
description: Dieser Artikel bietet eine Lösung für ein bekanntes Adobe Commerce 2.4.0-Problem, bei dem Zahlungsmethoden fehlen, wenn Kunden **Zurück zum standardmäßigen Checkout** verwenden, nachdem sie die Amazon-Zahlung aktiviert haben.
exl-id: efd792c7-8970-4366-b9d1-4bf284ea96db
feature: B2B, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# Bekanntes Problem in Adobe Commerce 2.4.0: Amazon-Zahlung, keine Zahlungsmethoden

Dieser Artikel bietet eine Lösung für ein bekanntes Problem mit Adobe Commerce 2.4.0, bei dem Zahlungsmethoden fehlen, wenn Kunden **Zurück zum standardmäßigen Checkout**, nachdem sie die Amazon-Bezahlung aktiviert haben.

## Betroffene Produkte und Versionen

Adobe Commerce On-Premise und Adobe Commerce auf Cloud-Infrastruktur v2.3.5.p1 und v2.4.0

<u>Zu reproduzierende Schritte:</u>

1. Navigieren Sie zur Storefront.
1. Fügen Sie beliebige Artikel zum Warenkorb hinzu und fahren Sie mit dem Checkout fort.
1. Melden Sie sich bei Ihrem Amazon Pay-Konto an.
1. Wählen Sie eine Adresse aus und fahren Sie mit dem Checkout fort.
1. Klicks **Zurück zum standardmäßigen Checkout**.
1. Fahren Sie mit dem Checkout fort.

<u>Erwartete Ergebnisse:</u>

Zahlungsmethoden sollten nach einem Neustart des Checkout angezeigt werden.

<u>Ergebnisse:</u>

Zahlungsmethoden fehlen.

## Lösung

Für Version 2.4.1 ist eine Lösung geplant.

## Verwandte Lesungen in unserer Wissensdatenbank:

* [Bekanntes Problem mit Adobe Commerce 2.4.0: Fehlermeldung bei Auswahl der lokalen Zahlungsmethode, die für einige Länder beim Checkout angezeigt wird](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: 404-Fehler beim Entfernen von Belohnungspunkten beim Checkout mit mehreren Sendungen](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Bestellungen zeigen Fehler an](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0 B2B Admin kann kein konfigurierbares Produkt zum Anführungszeichen hinzufügen](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Braintree-Zahlungsmethoden werden beim Checkout für mehrere Adressen nicht angezeigt](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Bekanntes Problem bei der Erstellung von Versandbeschriftungen in Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0 - Aktualisierung der Kundenaktivitäten funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0 - Exportsteuersätze funktionieren nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Schaltfläche &quot;Auswahl zum Warenkorb hinzufügen&quot;funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Rohdaten werden in Storefront angezeigt](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
