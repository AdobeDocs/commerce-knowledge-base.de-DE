---
title: 'Adobe Commerce 2.4.0, 2.4.1: Braintree Venmo-Teilrechnung aktivieren'
description: In diesem Artikel wird ein bekanntes Problem mit Adobe Commerce 2.4.0 und 2.4.1 beschrieben, bei dem für Bestellungen, die mit Braintree über Venmo aufgegeben werden, keine Teilrechnung verfügbar ist.
exl-id: ef6c8aa4-a2a7-4e07-a957-23173017baf2
feature: Invoices, Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 591c578b-908e-5b79-a9d3-931dfe60c24c
    internal-label: Invoices
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%
---
# Adobe Commerce 2.4.0, 2.4.1: Braintree Venmo-Teilrechnung aktivieren

In diesem Artikel wird ein bekanntes Problem mit Adobe Commerce 2.4.0 und 2.4.1 beschrieben, bei dem für Bestellungen, die mit Braintree über Venmo aufgegeben werden, keine Teilrechnung verfügbar ist.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises 2.4.0 und 2.4.1
* Adobe Commerce auf Cloud-Infrastrukturen 2.4.0 und 2.4.1

## Problem

<u>Voraussetzungen:</u>

Wählen Sie in der Konfiguration der Braintree-Zahlungsmethode **Venmo über Braintree aktivieren** = *Ja* mit **Zahlungsaktion** = *Autorisierung*; **Vault für Kartenzahlungen aktivieren** = *Nein*.

<u>Schritte zur Reproduktion:</u>

1. Erstellen Sie eine Bestellung für zwei oder mehr Produkte mit Venmo (Braintree) als Zahlungsmethode.
1. Öffnen Sie die Bestellung im Commerce Admin.
1. Erstellen Sie eine Rechnung für eines der bestellten Produkte.
1. Versuchen Sie, eine Rechnung für die restlichen bestellten Produkte zu erstellen.

<u>Erwartetes Ergebnis:</u>

Rechnung erstellt.

<u>Tatsächliches Ergebnis:</u>

Die folgende Fehlermeldung wird angezeigt: *Der Befehl „vault\_collection“ existiert nicht. Überprüfen Sie den Befehl und versuchen Sie es erneut.*

## Abhilfe

Erfassen Sie den gesamten Betrag bei der Erstellung von Rechnungen für Bestellungen, die mit Braintree über Venmo aufgegeben werden.
