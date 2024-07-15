---
title: '"Adobe Commerce 2.4.0 known issue: missing "Refund" label in Klarna"'
description: Dieser Artikel bietet eine Problemumgehung für ein bekanntes Problem in Admin für eine fehlende **Refund**-Beschriftung in Klarna VBE (Vendor Bundle Extension). Wenn im Klarna-Portal eine Rückerstattung durchgeführt wird, wird neben dem erstatteten gebündelten Produkt das **Rückerstattungsschild** nicht angezeigt.
exl-id: f08039b2-7f8b-481e-8ec8-1659e227744f
feature: B2B, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# Bekanntes Problem bei Adobe Commerce 2.4.0: fehlendes &quot;Refund&quot;-Label in Klarna

Dieser Artikel bietet eine Problemumgehung für ein bekanntes Problem in Admin für eine fehlende **Rückerstattungsbeschriftung** in Klarna VBE (Vendor Bundle Extension). Wenn im Klarna-Portal eine Rückerstattung durchgeführt wird, wird neben dem erstatteten gebündelten Produkt nicht das Etikett **Rückerstattung** angezeigt.

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort 2.4.0
* Adobe Commerce auf Cloud-Infrastruktur 2.4.0

## Problem

<u>Voraussetzungen:</u>

* Klarna ist aktiviert.
* Ein gebündeltes Produkt wird erstellt.

<u>Zu reproduzierende Schritte</u>

1. Gehen Sie zum Adobe Commerce-Frontend und fügen Sie ein gebündeltes Produkt zu **Warenkorb** hinzu.
1. Navigieren Sie zum Checkout.
1. Geben Sie Verbraucherinformationen zum Checkout ein und klicken Sie auf **Weiter**.
1. Wählen Sie **KP-Option** und klicken Sie auf **Bestellung platzieren**.
1. Gehen Sie zu **Admin** > **Verkauf** > **Bestellungen**.
1. Öffnen Sie die Bestellung.
1. Erstellen Sie eine Rechnung für das Produkt.
1. Wechseln Sie zu **Rechnungen** > **Rechnung auswählen** > Klicken Sie auf **Credit Memo** > Klicken Sie auf **Rückerstattungen** (Nicht auf **Offline zurückerstatteten**).
1. Gehen Sie zum Portal Klarna.
1. Öffnen Sie die Bestellung.
1. Die Bezeichnung **Refund** ist vorhanden.

<u>Erwartetes Ergebnis</u>

Auf dem Klarna-Portal wird neben dem erstatteten Produkt die Bezeichnung **Refund** angezeigt.

<u>Tatsächliches Ergebnis</u>

Auf dem Klarna-Portal wird neben dem erstatteten Produkt nicht die Bezeichnung **Refund** angezeigt.

## Workaround

Die Lösung für dieses Problem besteht darin, die fehlende **Rückerstattungsbeschriftung** im Klarna-Portal für rückerstattete gebündelte Produkte zu ignorieren. Die Rückerstattung erfolgte, auch wenn die Beschriftung **Rückerstattung** nicht angezeigt wurde. Das Problem wird voraussichtlich in Adobe Commerce 2.4.1 behoben, das für das 4. Quartal 2020 geplant ist.

## Verwandte Lesungen in unserer Wissensdatenbank:

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
