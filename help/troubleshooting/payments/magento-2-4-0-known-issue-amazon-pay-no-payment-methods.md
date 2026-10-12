---
title: 'Adobe Commerce 2.4.0 Bekanntes Problem: Amazon Bezahlen, keine Zahlungsmethoden'
description: Dieser Artikel bietet eine Lösung für ein bekanntes Problem in Adobe Commerce 2.4.0, bei dem Zahlungsmethoden fehlen, wenn Kundinnen und Kunden **Zur standardmäßigen Kasse zurückkehren** verwenden, nachdem sie Amazon Pay aktiviert haben.
exl-id: efd792c7-8970-4366-b9d1-4bf284ea96db
feature: B2B, Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%
---
# Adobe Commerce 2.4.0 Bekanntes Problem: Amazon Bezahlen, keine Zahlungsmethoden

Dieser Artikel bietet eine Lösung für ein bekanntes Problem in Adobe Commerce 2.4.0, bei dem Zahlungsmethoden fehlen, wenn Kundinnen und Kunden **Zur standardmäßigen Kasse zurückkehren** verwenden, nachdem sie Amazon Pay aktiviert haben.

## Betroffene Produkte und Versionen

Adobe Commerce On-Premises und Adobe Commerce on Cloud Infrastructure v2.3.5.p1 und v2.4.0

<u>Schritte zur Reproduktion:</u>

1. Navigieren Sie zur Storefront.
1. Fügen Sie einen beliebigen Artikel zum Warenkorb hinzu und fahren Sie mit der Kasse fort.
1. Melden Sie sich bei Ihrem Amazon Pay-Konto an.
1. Wählen Sie eine Adresse aus und fahren Sie mit der Kasse fort.
1. Klicken Sie **Zurück zur standardmäßigen**).
1. Fahren Sie mit der Kasse fort.

<u>Erwartete Ergebnisse:</u>

Zahlungsmethoden sollten nach dem Neustart des Checkouts angezeigt werden.

<u>Tatsächliche Ergebnisse:</u>

Zahlungsmethoden fehlen.

## Lösung

Für 2.4.1 ist eine Lösung geplant.

## Weiterführende Informationen finden Sie in unserer Support-Wissensdatenbank:

* [Bekanntes Problem mit Adobe Commerce 2.4.0: Fehlermeldung bei Auswahl der lokalen Zahlungsmethode, die für einige Länder während des Checkouts angezeigt wird](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0 Bekanntes Problem: Braintree-Zahlungsmethoden werden beim Checkout für mehrere Adressen nicht angezeigt](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
