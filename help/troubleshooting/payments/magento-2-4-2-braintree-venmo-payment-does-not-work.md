---
title: 'Adobe Commerce 2.4.2: Braintree Venmo Zahlung funktioniert nicht'
description: In diesem Artikel wird ein bekanntes Adobe Commerce 2.4.2-Problem beschrieben, bei dem keine Bestellungen generiert werden, wenn beim Checkout Braintree Venmo verwendet wird. Derzeit ist keine Lösung verfügbar.
exl-id: 1832ab64-5024-444b-915e-473b34979a6e
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Adobe Commerce 2.4.2: Braintree Venmo Zahlung funktioniert nicht

In diesem Artikel wird ein bekanntes Adobe Commerce 2.4.2-Problem beschrieben, bei dem keine Bestellungen generiert werden, wenn beim Checkout Braintree Venmo verwendet wird. Derzeit ist keine Lösung verfügbar.

## Betroffene Produkte und Versionen

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

## Problem

<u>Voraussetzung</u> :

Venmo-Zahlung in der Braintree-Konfiguration aktivieren.

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

Die Bestellung wird in Adobe Commerce erstellt, nachdem der Kunde von der Venmo-App zurück zum Store geleitet wurde, und die Bestellung wird wie erwartet auf Braintree erstellt.

## Lösung

Derzeit ist keine Lösung verfügbar.
