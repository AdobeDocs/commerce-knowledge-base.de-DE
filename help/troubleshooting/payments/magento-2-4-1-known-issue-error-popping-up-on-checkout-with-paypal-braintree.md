---
title: 'Bekanntes Problem in Adobe Commerce 2.4.1: Fehler beim Bestellen mit PayPal Braintree'
description: In diesem Artikel wird ein bekanntes Adobe Commerce 2.4.1-Problem beschrieben, bei dem eine Fehlermeldung beim Abrechnungsschritt der Kasse angezeigt wird, wenn eine PayPal-Braintree-Zahlung verwendet wird und mehrere Versandadressen ausgewählt wurden.
exl-id: db3830b2-4885-4d89-85cd-bdcbd4b396e6
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Bekanntes Problem in Adobe Commerce 2.4.1: Fehler beim Bestellen mit PayPal Braintree

In diesem Artikel wird ein bekanntes Adobe Commerce 2.4.1-Problem beschrieben, bei dem eine Fehlermeldung beim Abrechnungsschritt der Kasse angezeigt wird, wenn eine PayPal-Braintree-Zahlung verwendet wird und mehrere Versandadressen ausgewählt wurden.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.4.1
* Adobe Commerce On-Premises 2.4.1

## Problem

Wenn PayPal-Braintree-Zahlung verwendet wird und mehrere Versandadressen ausgewählt wurden, wird beim Abrechnungsschritt der Kasse eine Fehlermeldung angezeigt und ausgeblendet.

<u>Schritte zur Reproduktion:</u>

1. Melden Sie sich in der Storefront als Kunde an (optional kann es sich um einen Gast-Checkout handeln, wenn er in Admin aktiviert ist).
1. Fügen Sie ein Produkt zum Warenkorb hinzu.
1. Klicken, um die Warenkorbvorschau zu öffnen.
1. Klicken Sie **Warenkorb anzeigen und bearbeiten**.
1. Klicken Sie auf der Warenkorbseite auf **Mit mehreren Adressen auschecken**.
1. Klicken Sie **Zu Versandinformationen gehen** und geben Sie die Adressen an.
1. Klicken Sie **Weiter zu Rechnungsinformationen**.
1. Wählen Sie **PayPal-Braintree** und klicken Sie auf die Schaltfläche **PayPal**.
1. Klicken Sie im Popup-Fenster auf **Zustimmen und bezahlen**.

<u>Erwartetes Ergebnis:</u>

Die Bestellung erfolgt fehlerfrei.

<u>Tatsächliches Ergebnis:</u>

Die Bestellung wird aufgegeben, jedoch mit einem Fehler. Der *PayPal-Checkout konnte nicht initialisiert werden. Bitte kontaktieren Sie den Geschäftsinhaber*.  Der Fehler wird eine Sekunde lang angezeigt und verschwindet.

## Fehlerbehebung

Da die Auftragserteilung nicht blockiert wird, müssen keine Problemumgehungsschritte ausgeführt werden.
