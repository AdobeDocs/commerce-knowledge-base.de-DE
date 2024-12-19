---
title: 'Adobe Commerce 2.4.0, 2.4.1: Braintree Venmo Teilrechnung aktivieren'
description: In diesem Artikel wird ein bekanntes Adobe Commerce 2.4.0- und 2.4.1-Problem beschrieben, bei dem für Bestellungen, die mit dem Braintree über Venmo aufgegeben werden, keine Teilrechnung verfügbar ist.
exl-id: ef6c8aa4-a2a7-4e07-a957-23173017baf2
feature: Invoices, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Adobe Commerce 2.4.0, 2.4.1: Braintree Venmo Teilrechnung aktivieren

In diesem Artikel wird ein bekanntes Adobe Commerce 2.4.0- und 2.4.1-Problem beschrieben, bei dem für Bestellungen, die mit dem Braintree über Venmo aufgegeben werden, keine Teilrechnung verfügbar ist.

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

Erfassen Sie den gesamten Betrag bei der Erstellung von Rechnungen für Bestellungen per Braintree über Venmo.
