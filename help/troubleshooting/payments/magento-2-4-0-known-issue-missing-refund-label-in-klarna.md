---
title: 'Bekanntes Problem in Adobe Commerce 2.4.0: fehlende Kennzeichnung „Rückerstattung“ in Klarna'
description: Dieser Artikel bietet eine Problemumgehung für ein bekanntes Problem in Admin wegen eines fehlenden **Refund**-Labels in Klarna VBE (Vendor Bundled Extension). Bei der Durchführung einer Rückerstattung im Klarna-Portal wird das **Refund**-Label nicht neben dem zurückerstatteten Paket-Produkt angezeigt.
exl-id: f08039b2-7f8b-481e-8ec8-1659e227744f
feature: B2B, Orders, Payments
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Bekanntes Problem in Adobe Commerce 2.4.0: fehlende Kennzeichnung „Rückerstattung“ in Klarna

Dieser Artikel bietet eine Problemumgehung für ein bekanntes Problem in Admin wegen eines fehlenden **Refund**-Labels in Klarna VBE (Vendor Bundled Extension). Bei der Durchführung einer Rückerstattung im Klarna-Portal wird das **Rückerstattung**-Label nicht neben dem zurückerstatteten Paket-Produkt angezeigt.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises 2.4.0
* Adobe Commerce auf Cloud-Infrastruktur 2.4.0

## Problem

<u>Voraussetzungen:</u>

* Klarna ist aktiviert.
* Ein gebündeltes Produkt wird erstellt.

<u>Schritte zur Reproduktion</u>

1. Wechseln Sie zum Adobe Commerce-Frontend und fügen Sie ein gebündeltes Produkt zum **hinzu**.
1. Navigieren Sie zur Kasse.
1. Geben Sie Verbraucherinformationen in die Kasse ein und klicken Sie auf **Weiter**.
1. Wählen Sie **KP-Option** und klicken Sie auf **Bestellung aufgeben**.
1. Wechseln Sie **Admin** > **Verkauf** > **Bestellungen**.
1. Öffnen Sie die Bestellung.
1. Rechnung für das Produkt erstellen.
1. Wechseln Sie zu **Rechnungen** > **Rechnung auswählen** > Klicken Sie auf **Gutschrift** > Klicken Sie auf **Rückerstattung** (nicht **Rückerstattung offline**).
1. Zum Klarna-Portal.
1. Öffnen Sie die Bestellung.
1. Das **Refund**-Label ist vorhanden.

<u>Erwartetes Ergebnis</u>

Auf dem Klarna-Portal **neben dem** Produkt das Label „Rückerstattung“ angezeigt.

<u>Tatsächliches Ergebnis</u>

Auf dem Klarna-Portal **das** „Rückerstattung“ nicht neben dem zurückerstatteten Produkt angezeigt.

## Abhilfe

Die Problemumgehung besteht darin, das fehlende **Refund**-Label im Klarna-Portal für zurückerstattete gebündelte Produkte zu ignorieren. Die Rückerstattung ist erfolgt, obwohl das **Rückerstattung**-Label nicht angezeigt wurde. Das Problem wird voraussichtlich in Adobe Commerce 2.4.1 behoben, das im 4. Quartal 2020 veröffentlicht werden soll.

## Weiterführende Informationen finden Sie in unserer Support-Wissensdatenbank:

* [Bekanntes Problem in Adobe Commerce 2.4.0: Rohnachrichtendaten werden in der Storefront angezeigt](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0 Bekanntes Problem: Exportsteuersätze funktionieren nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 Bekanntes Problem: Braintree-Zahlungsmethoden werden beim Checkout für mehrere Adressen nicht angezeigt](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Fehlermeldung bei Auswahl der lokalen Zahlungsmethode, die für einige Länder während des Checkouts angezeigt wird](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: 404-Fehler beim Entfernen von Prämienpunkten beim Checkout für mehrere Sendungen](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Fehler bei der Anzeige von Bestellungen](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0 B2B-Admin kann kein konfigurierbares Produkt zum Angebot hinzufügen](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0 - Aktualisierung der Aktivitäten des Kunden funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Die Schaltfläche „Auswahl zu meinem Warenkorb hinzufügen“ funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
