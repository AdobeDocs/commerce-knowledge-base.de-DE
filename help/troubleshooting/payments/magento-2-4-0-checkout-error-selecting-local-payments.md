---
title: 'Adobe Commerce 2.4.0: Checkout-Fehler bei Auswahl lokaler Zahlungen'
description: 'In diesem Artikel wird über eine Lösung für ein bekanntes Problem in Adobe Commerce beim Checkout gesprochen, bei dem bei der Auswahl einer lokalen Zahlungsmethode für einige Länder eine Fehlermeldung angezeigt wird. Dies geschieht in den folgenden Ländern: Belgien, Italien, Niederlande, Polen und Spanien.'
exl-id: de2eafb0-d03c-4ff8-9615-0f2676d95848
feature: B2B, Categories, Checkout, Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '301'
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

Die Fehlermeldung &quot;*Es sind derzeit keine Zahlungsmethoden verfügbar. Bitte aktualisieren Sie Ihre Rechnungsadresse.*&quot; angezeigt wird, aber die lokalen Zahlungsmethoden werden weiterhin korrekt angezeigt und funktionieren.

## Lösung

Die Lösung besteht darin, die angezeigte Fehlermeldung zu ignorieren und die Zahlung wie gewohnt fortzusetzen, da alle lokalen Zahlungsmethoden normal funktionieren. Die Fehlerbehebung war ab Adobe Commerce Version 2.4.1 verfügbar.

## Verwandtes Lesen

* [Adobe Commerce 2.4.0 Bekanntes Problem: Braintree-Zahlungsmethoden werden beim Checkout für mehrere Adressen nicht angezeigt](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
