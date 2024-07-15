---
title: '''Bekanntes Problem mit Adobe Commerce 2.4.0: Schaltfläche "Neues Sortiment erstellen"fehlt'
description: Dieser Artikel bietet eine Behelfslösung für ein bekanntes Problem in der Commerce-Admin für zwei fehlende Schaltflächen auf der Seite zur Bestellerstellung. Beim Erstellen einer neuen Bestellung für einen neuen oder vorhandenen Kunden ist es nicht möglich, Produkte zur Bestellung aus dem Katalog hinzuzufügen, da die Schaltflächen **Produkte über SKU hinzufügen** und **Produkte hinzufügen** fehlen. Dies wird durch die Aktivierung des JS-Bundles verursacht. In Adobe Commerce 2.4.1 ist eine Fehlerbehebung verfügbar.
exl-id: 24ae880e-6d74-4444-9165-2744b12af81a
feature: B2B
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# Bekanntes Problem mit Adobe Commerce 2.4.0: Schaltfläche &quot;Neue Bestellung erstellen&quot;fehlt

Dieser Artikel bietet eine Behelfslösung für ein bekanntes Problem in der Commerce-Admin für zwei fehlende Schaltflächen auf der Seite zur Bestellerstellung. Beim Erstellen einer neuen Bestellung für einen neuen oder vorhandenen Kunden ist es nicht möglich, Produkte zur Bestellung aus dem Katalog hinzuzufügen, da die Schaltflächen **Produkte von SKU hinzufügen** und **Produkte hinzufügen** fehlen. Dies wird durch die Aktivierung des JS-Bundles verursacht. In Adobe Commerce 2.4.1 ist eine Fehlerbehebung verfügbar.

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort 2.4.0
* Adobe Commerce auf Cloud-Infrastruktur 2.4.0

## Problem

<u>Zu reproduzierende Schritte</u>

1. Wechseln Sie zu **Kunden > Alle Kunden**.
1. Klicken Sie auf den Link **Bearbeiten** eines Kunden.
1. Klicken Sie auf die Schaltfläche **Bestellung erstellen** .

<u>Erwartetes Ergebnis</u>

Die Schaltflächen **Produkte nach SKU hinzufügen** und **Produkte hinzufügen** werden auf der Seite **Neue Bestellung erstellen** angezeigt.

<u>Tatsächliches Ergebnis</u>

Die Schaltflächen **Produkte nach SKU hinzufügen** und **Produkte hinzufügen** fehlen auf der Seite **Neue Bestellung erstellen** .

## Workaround

Die Lösung für dieses Problem besteht darin, das JS-Bundling für die Adobe Commerce-Instanz zu deaktivieren. Das Problem wird voraussichtlich in Adobe Commerce 2.4.1 behoben, das für das 4. Quartal 2020 geplant ist.

## Verwandte Lesungen in unserer Wissensdatenbank

* [Bekanntes Problem mit Adobe Commerce 2.4.0: Rohdaten werden in Storefront angezeigt](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Exportsteuersätze funktionieren nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Braintree-Zahlungsmethoden werden beim Checkout für mehrere Adressen nicht angezeigt](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Fehlermeldung bei Auswahl der lokalen Zahlungsmethode, die für einige Länder beim Checkout angezeigt wird](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: 404-Fehler beim Entfernen von Belohnungspunkten beim Checkout mit mehreren Sendungen](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Bestellungen zeigen Fehler an](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0 B2B Admin kann kein konfigurierbares Produkt zum Anführungszeichen hinzufügen](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Bekanntes Problem bei der Erstellung von Versandbeschriftungen in Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0 - Aktualisierung der Kundenaktivitäten funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Schaltfläche &quot;Auswahl zum Warenkorb hinzufügen&quot;funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
