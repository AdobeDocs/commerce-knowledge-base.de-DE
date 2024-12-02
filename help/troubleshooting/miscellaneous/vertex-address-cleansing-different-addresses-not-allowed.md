---
title: 'Reklamationsbereinigung: Verschiedene Adressen sind nicht zulässig'
description: In diesem Artikel wird über die Lösung für das Problem gesprochen, bei dem der Benutzer versucht, eine **andere** Abrechnungs- und Versandadresse einzugeben, bei der die Überprüfung der Vertex-Adresse aktiviert ist, die Storefront den Benutzer nicht zur Eingabe berechtigt.
exl-id: a481b044-3b74-4792-abc6-249a182c49e1
feature: B2B, Orders, Shipping/Delivery, Checkout
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# Reklamationsbereinigung: Verschiedene Adressen sind nicht zulässig

In diesem Artikel wird über die Lösung für das Problem gesprochen, bei dem der Benutzer versucht, eine **andere** Abrechnungs- und Versandadresse einzugeben, wobei die Überprüfung der Vertex-Adresse aktiviert ist, die Storefront den Benutzer nicht zur Eingabe berechtigt.

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort und Adobe Commerce über Cloud-Infrastruktur 2.3.5-p1

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu Admin > **Geschäfte** > **Konfiguration** > **Verkauf** > **Adressbereinigung**.
1. Wählen Sie *Aktiviert* aus der Dropdown-Liste **Vertextsadressenbereinigung verwenden** und **Konfiguration speichern** aus.
1. Gehen Sie als Gast in das Frontend und fügen Sie dem Warenkorb ein Produkt hinzu.
1. Klicken Sie auf das Warenkorbsymbol und **Fahren Sie mit dem Checkout fort**.
1. Füllen Sie die Adressfelder aus.
1. Wählen Sie die gewünschte **Versandmethode** aus und klicken Sie auf **Weiter**.
1. Klicken Sie erneut auf die Schaltfläche **Weiter** .
1. Deaktivieren Sie **Meine Abrechnungs- und Lieferadresse** **sind identisch** und geben Sie eine neue Abrechnungsadresse ein (die sich von Adresse unterscheidet).
1. Klicken Sie auf die Schaltfläche **Aktualisieren** und dann auf **Adresse aktualisieren**.

<u>Erwartete Ergebnisse</u>:

Der Benutzer sieht verschiedene Abrechnungs- und Versandadressen.

<u>Tatsächliche Ergebnisse</u>:

Wenn der Benutzer die Aktualisierung durchführt, werden die Abrechnungs- und Versandadressen wieder identisch.

## Ursache

Die Verifizierung der Testadressen ist fehlgeschlagen.

## Lösung

Deaktivieren Sie die Verifizierung der Vertex-Adresse oder aktualisieren Sie auf Version 2.4.0.

## Verwandtes Lesen

* [Bekanntes Problem mit Adobe Commerce 2.4.0: Fehlermeldung bei Auswahl der lokalen Zahlungsmethode, die für einige Länder beim Checkout angezeigt wird](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: 404-Fehler beim Entfernen von Belohnungspunkten beim Checkout mit mehreren Sendungen](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Bestellungen zeigen Fehler an](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0 B2B Admin kann kein konfigurierbares Produkt zum Anführungszeichen hinzufügen](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Braintree-Zahlungsmethoden werden beim Checkout für mehrere Adressen nicht angezeigt](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0 - Aktualisierung der Kundenaktivitäten funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0 - Exportsteuersätze funktionieren nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Schaltfläche &quot;Auswahl zum Warenkorb hinzufügen&quot;funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Rohdaten werden in Storefront angezeigt](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Bekanntes Problem bei Adobe Commerce 2.4.0: fehlendes &quot;Refund&quot;-Label in Klarna](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Zwei Schaltflächen fehlen auf der Seite &quot;Neue Bestellung erstellen&quot;in Admin](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-create-new-order-buttons-missing.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Wenn Braintree aktiviert ist, Problem mit partieller Venmo-Rechnung](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Fehlermeldung bei Auswahl der lokalen Zahlungsmethode, die für einige Länder beim Checkout angezeigt wird](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Amazon-Pay-fähig, Zahlungsmethoden fehlen bei Rückkehr zum Standard-Checkout, verwendet](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: 2.4.0-Installation schlägt mit veraltetem Speicher-Cache fehl](/help/troubleshooting/installation-and-upgrade/magento-2-4-0-known-issue-2-4-0-installation-fails-with-outdated-stores-cache.md)
