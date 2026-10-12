---
title: 'Adobe Commerce 2.4.2: Braintree Venmo-Zahlung funktioniert nicht'
description: In diesem Artikel wird ein bekanntes Adobe Commerce 2.4.2-Problem beschrieben, bei dem keine Bestellungen generiert werden, wenn beim Checkout Braintree Venmo verwendet wird. Derzeit ist keine Lösung verfügbar.
exl-id: 1832ab64-5024-444b-915e-473b34979a6e
feature: Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%
---
# Adobe Commerce 2.4.2: Braintree Venmo-Zahlung funktioniert nicht

In diesem Artikel wird ein bekanntes Adobe Commerce 2.4.2-Problem beschrieben, bei dem keine Bestellungen generiert werden, wenn beim Checkout Braintree Venmo verwendet wird. Derzeit ist keine Lösung verfügbar.

## Betroffene Produkte und Versionen

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

## Problem

<u>Voraussetzung</u> :

Aktivieren der Venmo-Zahlung in der Braintree-Konfiguration.

<u>Schritte zur Reproduktion</u> :

1. Fügen Sie in der Storefront einen beliebigen Artikel zum Warenkorb hinzu.
1. Fahren Sie mit **Checkout** fort.
1. Wählen Sie die entsprechende Versandart aus.
1. Wählen Sie **Venmo** als Zahlungsmethode aus.
1. Klicken Sie **Mit Venmo bezahlen**.
1. Klicken Sie **Bestellung aufgeben**.

<u>Tatsächliche Ergebnisse</u>:

Die Bestellung wird nicht im Adobe Commerce-Code erstellt, nachdem der Kunde von der Venmo-App zurück zum Store weitergeleitet wurde, und es wird keine Fehlermeldung angezeigt. Die Bestellung wird in Braintree erstellt.

<u>Erwartete Ergebnisse</u>:

Die Bestellung wird in Adobe Commerce erstellt, nachdem der Kunde von der Venmo-App zurück zum Store weitergeleitet wurde, und die Bestellung wird wie erwartet in Braintree erstellt.

## Lösung

Derzeit ist keine Lösung verfügbar.
