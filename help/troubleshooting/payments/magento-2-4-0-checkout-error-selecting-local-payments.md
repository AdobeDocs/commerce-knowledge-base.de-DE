---
title: 'Adobe Commerce 2.4.0: Checkout-Fehler bei Auswahl lokaler Zahlungen'
description: In diesem Artikel wird über eine Lösung für ein bekanntes Problem in Adobe Commerce beim Checkout gesprochen, bei dem eine Fehlermeldung angezeigt wird, wenn eine lokale Zahlungsmethode für einige Länder ausgewählt wird. Dies trifft auf die Länder Belgien, Italien, Niederlande, Polen und Spanien zu.
exl-id: de2eafb0-d03c-4ff8-9615-0f2676d95848
feature: B2B, Categories, Checkout, Orders, Payments
role: Developer
source-git-commit: 77f41d6034f985794e5c5b89cc007a69858683b9
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: Checkout-Fehler bei Auswahl lokaler Zahlungen

In diesem Artikel wird über eine Lösung für ein bekanntes Problem in Adobe Commerce beim Checkout gesprochen, bei dem eine Fehlermeldung angezeigt wird, wenn eine lokale Zahlungsmethode für einige Länder ausgewählt wird. Dies trifft auf die Länder Belgien, Italien, Niederlande, Polen und Spanien zu.

Die Fehlermeldung &quot;*Es sind derzeit keine Zahlungsmethoden verfügbar. Bitte aktualisieren Sie Ihre Rechnungsadresse.*&quot; angezeigt, aber die lokalen Zahlungsmethoden werden weiterhin angezeigt und funktionieren ordnungsgemäß. In Adobe Commerce 2.4.1 wird eine permanente Korrektur verfügbar sein.

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort 2.4.0
* Adobe Commerce auf Cloud-Infrastruktur 2.4.0

## Problem

<u>Voraussetzungen</u>:

* Adobe Commerce 2.4.0 ist installiert.
* Erstellen Sie ein Produkt und eine Kategorie.
* Konfigurieren Sie die [Braintree-Zahlungsmethode](https://developer.adobe.com/commerce/webapi/graphql/payment-methods/braintree/).

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zur Storefront.
1. Wählen Sie Elemente aus, die dem Warenkorb hinzugefügt werden sollen.
1. Fahren Sie mit dem Checkout fort.
1. Füllen Sie das Adressformular mit einer gültigen Adresse aus.
1. Fahren Sie mit der Seite Überprüfen und Zahlungen fort.

<u>Erwartetes Ergebnis</u>:

Die lokalen Zahlungsmethoden sollten normal angezeigt werden, ohne dass eine Fehlermeldung angezeigt wird.

<u>Tatsächliches Ergebnis</u>:

Die Fehlermeldung &quot;*Es sind derzeit keine Zahlungsmethoden verfügbar. Bitte aktualisieren Sie Ihre Rechnungsadresse.*&quot; angezeigt, aber die lokalen Zahlungsmethoden werden weiterhin angezeigt und funktionieren ordnungsgemäß.

## Lösung

Die Lösung besteht darin, die angezeigte Fehlermeldung zu ignorieren und die Zahlung wie gewohnt fortzusetzen, da alle lokalen Zahlungsmethoden normal funktionieren. Die Fehlerbehebung war ab Adobe Commerce-Version 2.4.1 verfügbar.

## Verwandtes Lesen

* [Bekanntes Problem mit Adobe Commerce 2.4.0: Rohdaten werden in Storefront angezeigt](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Exportsteuersätze funktionieren nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Braintree-Zahlungsmethoden werden beim Checkout für mehrere Adressen nicht angezeigt](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Aktualisierung der Kundenaktivitäten nicht möglich](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 B2B Admin kann kein konfigurierbares Produkt zum Anführungszeichen hinzufügen](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
