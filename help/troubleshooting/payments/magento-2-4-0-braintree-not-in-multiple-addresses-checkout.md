---
title: 'Adobe Commerce 2.4.0: Braintree nicht am Checkout für mehrere Adressen'
description: Dieser Artikel bietet eine Problemumgehung für ein bekanntes Problem in Adobe Commerce 2.4.0, bei dem Braintree-Zahlungsmethoden nicht in die Arbeit mit dem Checkout für mehrere Adressen einbezogen sind. Beachten Sie, dass das Problem in Adobe Commerce 2.4.1 behoben wurde.
exl-id: efde0bba-fd4a-490b-becb-856cb9ea58a5
feature: Checkout, Compliance, Orders, Payments, Shipping/Delivery
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: 04d3134c-2afb-5bd7-ac14-e19fa935e848
    internal-label: Shipping/Delivery
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%
---
# Adobe Commerce 2.4.0: Braintree nicht am Checkout für mehrere Adressen

Dieser Artikel bietet eine Problemumgehung für ein bekanntes Problem in Adobe Commerce 2.4.0, bei dem Braintree-Zahlungsmethoden nicht in die Arbeit mit dem Checkout für mehrere Adressen einbezogen sind. Beachten Sie, dass das Problem in Adobe Commerce 2.4.1 behoben wurde.

Hinweis: Adobe Commerce empfiehlt die Verwendung der [Commerce Marketplace Braintree-Erweiterung](https://marketplace.magento.com/paypal-module-braintree.html) für Version 2.3 und höher, um die PSD-Konformität zu wahren. Die Erweiterung bietet nicht die Funktion zum Auschecken über mehrere Adressen.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premise v2.4.0
* Adobe Commerce auf Cloud-Infrastruktur v2.4.0

## Problem

<u>Voraussetzungen</u>:

Die Braintree-Kernintegration wird verwendet.

<u>Schritte zur Reproduktion</u>:

1. Geh zum Laden.
1. Melden Sie sich als Kunde an.
1. Fügen Sie ein Produkt zum Warenkorb hinzu.
1. Öffnen Sie den Warenkorb.
1. Drücken Sie **Warenkorb anzeigen und bearbeiten**.
1. Drücken Sie **Mit mehreren Adressen auschecken**.
1. Drücken Sie **Zu Versandinformationen gehen**.
1. Drücken Sie **Weiter zu Rechnungsinformationen**.

<u>Erwartetes Ergebnis</u>:

Braintree ist als Zahlungsmethode verfügbar.

<u>Tatsächliches </u>:

Braintree ist nicht als Zahlungsmethode verfügbar.

## Abhilfe

Aktivieren Sie keine Optionen für mehrere Adressen, wenn Sie Braintree in Adobe Commerce 2.4.0 verwenden. Dieses Problem wurde in Adobe Commerce 2.4.1 behoben.
