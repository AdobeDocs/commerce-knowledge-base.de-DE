---
title: 'Adobe Commerce 2.4.0, 2.4.1: Braintree Venmo-Teilrechnung aktivieren'
description: In diesem Artikel wird ein bekanntes Problem mit Adobe Commerce 2.4.0 und 2.4.1 beschrieben, bei dem keine Teilrechnung für Bestellungen verfügbar ist, die über Venmo mit Braintree bestellt wurden.
exl-id: ef6c8aa4-a2a7-4e07-a957-23173017baf2
feature: Invoices, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Adobe Commerce 2.4.0, 2.4.1: Braintree Venmo-Teilrechnung aktivieren

In diesem Artikel wird ein bekanntes Problem mit Adobe Commerce 2.4.0 und 2.4.1 beschrieben, bei dem keine Teilrechnung für Bestellungen verfügbar ist, die über Venmo mit Braintree bestellt wurden.

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort 2.4.0 und 2.4.1
* Adobe Commerce auf Cloud-Infrastruktur 2.4.0 und 2.4.1

## Problem

<u>Voraussetzungen:</u>

Legen Sie in der Konfiguration der Braintree-Zahlungsmethode **Venmo durch Braintree** = *Ja* mit **Zahlungsaktion** = *Autorisierung*; **Vault für Kartenzahlungen aktivieren** = *Nein* fest.

<u>Zu reproduzierende Schritte:</u>

1. Erstellen Sie eine Bestellung für zwei oder mehr Produkte unter Verwendung von Venmo (Braintree) als Zahlungsmethode.
1. Öffnen Sie die Bestellung in Commerce Admin.
1. Erstellen Sie eine Rechnung für eines der bestellten Produkte.
1. Versuchen Sie, eine Rechnung für die restlichen bestellten Produkte zu erstellen.

<u>Erwartetes Ergebnis:</u>

Rechnung erstellt.

<u>Tatsächliches Ergebnis:</u>

Die folgende Fehlermeldung wird angezeigt: *Der Befehl &quot;vault\_Capture&quot;ist nicht vorhanden. Überprüfen Sie den Befehl und versuchen Sie es erneut.*

## Workaround

Erfassen Sie den Gesamtbetrag bei der Erstellung von Rechnungen für Bestellungen, die über Venmo mit Braintree aufgegeben werden.
