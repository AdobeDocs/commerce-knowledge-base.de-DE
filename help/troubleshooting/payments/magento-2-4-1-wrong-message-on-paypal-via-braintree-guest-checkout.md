---
title: 'Adobe Commerce 2.4.1: Falsche Meldung beim PayPal-Braintree-Gast-Checkout'
description: In diesem Artikel wird ein bekanntes Adobe Commerce 2.4.1-Problem beschrieben, bei dem ein Gast, der versucht, über Braintree eine Bestellung bei PayPal aufzugeben, eine nicht-informative Fehlermeldung erhält, wenn der Gast-Checkout deaktiviert ist.
exl-id: 758f5c57-997e-4aca-b299-9934c94fa121
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 77f41d6034f985794e5c5b89cc007a69858683b9
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# Adobe Commerce 2.4.1: Falsche Meldung beim PayPal-Braintree-Gast-Checkout

In diesem Artikel wird ein bekanntes Adobe Commerce 2.4.1-Problem beschrieben, bei dem ein Gast, der versucht, über Braintree eine Bestellung bei PayPal aufzugeben, eine nicht-informative Fehlermeldung erhält, wenn der Gast-Checkout deaktiviert ist.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises 2.4.0, 2.4.1
* Adobe Commerce auf Cloud-Infrastruktur 2.4.0, 2.4.1

## Problem

Ein unspezifischer Fehler wird angezeigt, wenn der Gast-Checkout im Backend deaktiviert ist und die Zahlungsoption PayPal über Braintree aus dem Mini-Warenkorb oder Warenkorb ausgewählt wird.

<u>Voraussetzungen</u>:

1. Legen Sie im Commerce Admin unter **Stores** > **Configuration** > **Sales** > **Checkout** **Allow Guest Checkout** = *No* fest.
1. Aktivieren Sie PayPal per Braintree, wie in der [Braintree](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/payments/braintree?) in unserem Benutzerhandbuch beschrieben.

<u>Schritte zur Reproduktion</u>:

1. Produkt als Gast in den Warenkorb legen.
1. Wählen Sie **Mini-Warenkorb** und klicken Sie auf **Mit PayPal bezahlen**.
1. Schließen Sie den PayPal-Checkout ab und landen Sie dann auf der Seite „Bestellübersicht“.
1. Wählen Sie **Versandart**.
1. Klicken Sie **Bestellung aufgeben**.

<u>Erwartete Ergebnisse</u>:

Wenn ein Kunde auf die PayPal-Schaltfläche auf der Seite „Mini-Warenkorb“ oder „Warenkorb“ klickt, sollte dem Kunden die folgende Meldung angezeigt werden:

<pre><code class="language-bash">To check out, please sign in with your email address.</code></pre>

Wenn Sie Direct Paypal ohne Braintree aktivieren, verhält sich dieses Szenario anders. Der Gastbenutzer kann den Zahlungsprozess nicht fortsetzen. Wenn der Gastnutzer auf die PayPal-Schaltfläche im Mini-Warenkorb klickt, wird die folgende Meldung angezeigt:

<pre><code class="language-bash">To check out, please sign in with your email address.</code></pre>

<u>Tatsächliche Ergebnisse</u>:

Der Kunde wird zur Seite „Warenkorb“ weitergeleitet und die folgende Meldung wird angezeigt:

<pre><code class="language-bash">The customer email is missing. Enter and try again.</code></pre>

## Abhilfe

Die Problemumgehung besteht darin, dass sich der Kunde bei einem Store anmelden kann (angemeldete Benutzer verwenden keinen Gast-Checkout), bei dem der Gast-Checkout deaktiviert ist. Dieses Problem wurde in Adobe Commerce Version 2.4.2 behoben.

## Verwandtes Lesen

* [Best Practice für die Anzahl der in den Warenkorb befindlichen Produkte in Adobe Commerce](https://support.magento.com/hc/en-us/articles/360048550332) in unserer Support-Wissensdatenbank.
* [Tutorial zur Bestellabwicklung: Schritt 1. Artikel zum Warenkorb hinzufügen, ](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/order-add-items/) in unserer Entwicklerdokumentation
* [Tutorial zum GraphQL-Checkout: Schritt 1. Fügen Sie Produkte zum Warenkorb hinzu](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/add-product-to-cart/) in unserer Entwicklerdokumentation
