---
title: "Adobe Commerce 2.4.1: Falsche Nachricht beim PayPal-Braintree-Gast-Checkout"
description: In diesem Artikel wird ein bekanntes Adobe Commerce 2.4.1-Problem beschrieben, bei dem ein Gastkunden, der versucht, über Braintree eine Bestellung bei PayPal aufzugeben, eine nicht informative Fehlermeldung erhält, wenn der Gastkauf deaktiviert ist.
exl-id: 758f5c57-997e-4aca-b299-9934c94fa121
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# Adobe Commerce 2.4.1: Falsche Nachricht beim PayPal-Braintree-Gast-Checkout

In diesem Artikel wird ein bekanntes Adobe Commerce 2.4.1-Problem beschrieben, bei dem ein Gastkunden, der versucht, über Braintree eine Bestellung bei PayPal aufzugeben, eine nicht informative Fehlermeldung erhält, wenn der Gastkauf deaktiviert ist.

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort 2.4.0, 2.4.1
* Adobe Commerce auf Cloud-Infrastruktur 2.4.0, 2.4.1

## Problem

Ein unspezifischer Fehler wird angezeigt, wenn der Gast-Checkout aus dem Backend deaktiviert ist und die Option PayPal through Braintree Payment aus dem Mini-Warenkorb oder Warenkorb ausgewählt wird.

<u>Voraussetzungen</u>:

1. Legen Sie in Commerce Admin unter **Stores** > **Konfiguration** > **Verkauf** > **Checkout** den Wert **Gastauscheck zulassen** = *Nein* fest.
1. Aktivieren Sie PayPal über Braintree, wie im Benutzerhandbuch unter [Braintree](https://docs.magento.com/user-guide/payment/braintree.html?) beschrieben.

<u>Zu reproduzierende Schritte</u>:

1. Fügen Sie das Produkt als Gast zum Warenkorb hinzu.
1. Wählen Sie **Mini-Warenkorb** und klicken Sie auf **Mit PayPal bezahlen**.
1. Schließen Sie den Paypal-Checkout ab, und landen Sie dann auf der Seite &quot;Bestellübersicht&quot;.
1. Wählen Sie **Versandmethode** aus.
1. Klicken Sie auf **Bestellung platzieren**.

<u>Erwartete Ergebnisse</u>:

Wenn ein Kunde auf die Schaltfläche PayPal auf der Seite &quot;Mini-Warenkorb&quot;oder &quot;Warenkorb&quot;klickt, sollte dem Kunden die folgende Nachricht angezeigt werden:

<pre><code class="language-bash">To check out, please sign in with your email address.</code></pre>

Wenn Sie &quot;direct Paypal&quot;aktivieren, ohne Braintree zu verwenden, verhält sich dieses Szenario anders. Es ermöglicht dem Gastbenutzer nicht, den Zahlungsprozess fortzusetzen. Es wird die folgende Meldung angezeigt, wenn der Gastbenutzer auf die Schaltfläche PayPal im Mini-Warenkorb klickt:

<pre><code class="language-bash">To check out, please sign in with your email address.</code></pre>

<u>Tatsächliche Ergebnisse</u>:

Der Kunde wird zur Seite Warenkorb weitergeleitet und die folgende Meldung wird angezeigt:

<pre><code class="language-bash">The customer email is missing. Enter and try again.</code></pre>

## Workaround

Die Lösung für dieses Problem besteht darin, dass sich der Kunde in einem Speicher anmelden kann (angemeldete Benutzer verwenden keinen Gastkasse). wo der Gastkauf deaktiviert ist. Dieses Problem wurde in Adobe Commerce-Version 2.4.2 behoben.

## Verwandtes Lesen

* [Best Practice für die Anzahl der Produkte im Warenkorb in Adobe Commerce](https://support.magento.com/hc/en-us/articles/360048550332) in unserer Support-Wissensdatenbank.
* [Tutorial zur Bestellverarbeitung: Schritt 1. Hinzufügen von Artikeln zum Warenkorb](https://devdocs.magento.com/guides/v2.4/rest/tutorials/orders/order-add-items.html) in unserer Entwicklerdokumentation
* [Tutorial zum GraphQL-Checkout: Schritt 1. Produkte zum Warenkorb hinzufügen](https://devdocs.magento.com/guides/v2.4/graphql/tutorials/checkout/checkout-add-product-to-cart.html) in unserer Entwicklerdokumentation
