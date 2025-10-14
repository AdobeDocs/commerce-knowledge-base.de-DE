---
title: 'Adobe Commerce 2.4.0: Checkout-Fehler bei Auswahl lokaler Zahlungen'
description: 'In diesem Artikel wird über eine Lösung für ein bekanntes Problem in Adobe Commerce beim Checkout gesprochen, bei dem bei der Auswahl einer lokalen Zahlungsmethode für einige Länder eine Fehlermeldung angezeigt wird. Dies geschieht in den folgenden Ländern: Belgien, Italien, Niederlande, Polen und Spanien.'
exl-id: de2eafb0-d03c-4ff8-9615-0f2676d95848
feature: B2B, Categories, Checkout, Orders, Payments
role: Developer
source-git-commit: 9cd9720a73b8ecde3baf6a7a5b5732ad1330feee
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: Checkout-Fehler bei Auswahl lokaler Zahlungen

In diesem Artikel wird über eine Lösung für ein bekanntes Problem in Adobe Commerce beim Checkout gesprochen, bei dem bei der Auswahl einer lokalen Zahlungsmethode für einige Länder eine Fehlermeldung angezeigt wird. Dies geschieht in den folgenden Ländern: Belgien, Italien, Niederlande, Polen und Spanien.

Die Fehlermeldung &quot;*Es sind derzeit keine Zahlungsmethoden verfügbar. Bitte aktualisieren Sie Ihre Rechnungsadresse.*&quot; wird angezeigt, aber die lokalen Zahlungsmethoden werden weiterhin angezeigt und funktionieren ordnungsgemäß. In Adobe Commerce 2.4.1 ist eine dauerhafte Fehlerbehebung verfügbar.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises 2.4.0
* Adobe Commerce auf Cloud-Infrastruktur 2.4.0

## Problem

<u>Voraussetzungen</u>:

* Adobe Commerce 2.4.0 ist installiert.
* Erstellen Sie ein Produkt und eine Kategorie.
* [Braintree-Zahlungsmethode &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/payment-methods/braintree/).

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zur Storefront.
1. Artikel auswählen, die dem Warenkorb hinzugefügt werden sollen.
1. Zur Kasse gehen.
1. Füllen Sie das Adressformular mit einer gültigen Adresse aus.
1. Navigieren Sie zur Seite Überprüfen und Zahlungen .

<u>Erwartetes Ergebnis</u>:

Die lokalen Zahlungsmethoden sollten normal und ohne Fehlermeldung angezeigt werden.

<u>Tatsächliches </u>:

Die Fehlermeldung &quot;*Es sind derzeit keine Zahlungsmethoden verfügbar. Bitte aktualisieren Sie Ihre Rechnungsadresse.*&quot; angezeigt, die lokalen Zahlungsmethoden werden jedoch weiterhin korrekt angezeigt und funktionieren.

## Lösung

Die Lösung besteht darin, die angezeigte Fehlermeldung zu ignorieren und die Zahlung wie gewohnt fortzusetzen, da alle lokalen Zahlungsmethoden normal funktionieren. Die Fehlerbehebung war ab Adobe Commerce Version 2.4.1 verfügbar.

## Verwandtes Lesen

* [Adobe Commerce 2.4.0 Bekanntes Problem: Exportsteuersätze funktionieren nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 Bekanntes Problem: Braintree-Zahlungsmethoden werden beim Checkout für mehrere Adressen nicht angezeigt](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Aktualisierung der Aktivitäten des Kunden funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 B2B-Admin kann kein konfigurierbares Produkt zum Angebot hinzufügen](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
