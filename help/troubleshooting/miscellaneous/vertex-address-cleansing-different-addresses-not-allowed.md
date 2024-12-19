---
title: 'Vertex-Adressbereinigung: Verschiedene Adressen nicht zulässig'
description: In diesem Artikel wird die Lösung für das Problem beschrieben, dass Benutzende, die versuchen, eine **andere** Rechnungs- und Lieferadresse einzugeben, die Vertex-Adressvalidierung aktiviert haben, diese nicht von der Storefront eingeben lassen.
exl-id: a481b044-3b74-4792-abc6-249a182c49e1
feature: B2B, Orders, Shipping/Delivery, Checkout
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# Vertex-Adressbereinigung: Verschiedene Adressen nicht zulässig

In diesem Artikel wird die Lösung des Problems beschrieben, dass Benutzende, die versuchen, eine **andere** Rechnungs- und Lieferadresse einzugeben, die Vertex-Adressvalidierung aktiviert haben, diese nicht eingeben können.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises und Adobe Commerce on Cloud Infrastructure 2.3.5-p1

## Problem

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie zu Admin > **Stores** > **Konfiguration** > **Vertrieb** > **Adressbereinigung**.
1. Wählen Sie *Aktiviert* aus der Dropdown-Liste **Vertex-Adressbereinigung verwenden** und **Konfiguration speichern**.
1. Gehen Sie als Gast zum Frontend und fügen Sie dem Warenkorb ein Produkt hinzu.
1. Klicken Sie auf das Symbol Warenkorb und **Zur Kasse gehen**.
1. Füllen Sie die Adressfelder aus.
1. Wählen Sie die gewünschte **Versandart** aus und klicken Sie auf **Weiter**.
1. Klicken Sie erneut auf **Weiter**.
1. Deaktivieren Sie **Meine Abrechnungs- und****sind identisch** und geben Sie eine neue Abrechnungsadresse ein (nicht identisch mit Adresse).
1. Klicken Sie auf **Aktualisieren** und dann auf **Adresse aktualisieren**.

<u>Erwartete Ergebnisse</u>:

Der/die Benutzende sieht unterschiedliche Abrechnungs- und Versandadressen.

<u>Tatsächliche Ergebnisse</u>:

Wenn der Benutzer auf „Aktualisieren“ klickt, werden die Abrechnungs- und Versandadressen wieder identisch.

## Ursache

Die Verifizierung der Vertex-Adresse ist fehlgeschlagen.

## Lösung

Deaktivieren Sie die Verifizierung der Vertex-Adresse oder aktualisieren Sie auf 2.4.0.

## Verwandtes Lesen

* [Bekanntes Problem mit Adobe Commerce 2.4.0: Fehlermeldung bei Auswahl der lokalen Zahlungsmethode, die für einige Länder während des Checkouts angezeigt wird](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: 404-Fehler beim Entfernen von Prämienpunkten beim Checkout für mehrere Sendungen](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Fehler bei der Anzeige von Bestellungen](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0 B2B-Admin kann kein konfigurierbares Produkt zum Angebot hinzufügen](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0 Bekanntes Problem: Braintree-Zahlungsmethoden werden beim Checkout für mehrere Adressen nicht angezeigt](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0 - Aktualisierung der Aktivitäten des Kunden funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 bekanntes Problem - Exportsteuersätze funktionieren nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Die Schaltfläche „Auswahl zu meinem Warenkorb hinzufügen“ funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Rohnachrichtendaten werden in der Storefront angezeigt](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: fehlende Kennzeichnung „Rückerstattung“ in Klarna](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Auf der Seite „Neue Bestellung erstellen“ in „Admin“ fehlen zwei Schaltflächen](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-create-new-order-buttons-missing.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Wenn das Braintree aktiviert ist, liegt ein Problem mit der Venmo-Teilrechnung vor](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Fehlermeldung bei Auswahl der lokalen Zahlungsmethode, die für einige Länder während des Checkouts angezeigt wird](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0 Bekanntes Problem: Amazon Pay aktiviert, Zahlungsmethoden fehlen, wenn die Rückgabe zur standardmäßigen Kasse verwendet wird](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Die Installation von 2.4.0 schlägt mit veraltetem Speicher-Cache fehl](/help/troubleshooting/installation-and-upgrade/magento-2-4-0-known-issue-2-4-0-installation-fails-with-outdated-stores-cache.md)
