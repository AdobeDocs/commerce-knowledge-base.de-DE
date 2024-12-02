---
title: 'Bekanntes Problem in Adobe Commerce 2.4.1: Fehler beim Aufrufen des Checkouts mit PayPal-Braintree'
description: In diesem Artikel wird ein bekanntes Problem mit Adobe Commerce 2.4.1 beschrieben, bei dem eine Fehlermeldung angezeigt und im Abrechnungsschritt von Checkout ausgeblendet wird, wenn die PayPal-Braintree-Zahlung verwendet und mehrere Adressen gesendet werden.
exl-id: db3830b2-4885-4d89-85cd-bdcbd4b396e6
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Bekanntes Problem in Adobe Commerce 2.4.1: Fehler beim Aufrufen des Checkouts mit PayPal-Braintree

In diesem Artikel wird ein bekanntes Problem mit Adobe Commerce 2.4.1 beschrieben, bei dem eine Fehlermeldung angezeigt und im Abrechnungsschritt von Checkout ausgeblendet wird, wenn die PayPal-Braintree-Zahlung verwendet und mehrere Adressen gesendet werden.

## Betroffene Produkte und Versionen

* Adobe Commerce in Cloud-Infrastruktur 2.4.1
* Adobe Commerce vor Ort 2.4.1

## Problem

Eine Fehlermeldung wird angezeigt und verschwindet im Schritt &quot;Rechnungsstellung&quot;des Checkout, wenn die PayPal-Braintree-Zahlung verwendet und mehrere Adressen gesendet werden.

<u>Zu reproduzierende Schritte:</u>

1. Melden Sie sich auf der Storefront als Kunde an (optional kann es sich um einen Gast-Checkout handeln, wenn er in Admin aktiviert ist).
1. Fügen Sie dem Warenkorb ein Produkt hinzu.
1. Klicken Sie auf , um die Vorschau des Warenkorbs zu öffnen.
1. Klicken Sie auf **Warenkorb anzeigen und bearbeiten**.
1. Klicken Sie auf der Seite &quot;Warenkorb&quot;auf **Mit mehreren Adressen auschecken**.
1. Klicken Sie auf **Zu Versandinformationen wechseln** und geben Sie die Adressen an.
1. Klicken Sie auf **Weiter zu Rechnungsinformationen**.
1. Wählen Sie **PayPal Braintree** und klicken Sie auf die Schaltfläche **PayPal** .
1. Klicken Sie im Popup-Fenster auf **Zustimmen und Bezahlen**.

<u>Erwartetes Ergebnis:</u>

Die Bestellung wird ohne Fehler aufgegeben.

<u>Tatsächliches Ergebnis:</u>

Die Reihenfolge wird platziert, jedoch mit einem Fehler. Der *PayPal Checkout konnte nicht initialisiert werden. Bitte kontaktieren Sie den Store-Eigentümer*.  -Fehler wird für eine Sekunde angezeigt und verschwindet.

## Fehlerbehebung

Da die Bestellplatzierung nicht blockiert wird, müssen keine Problemumgehungsschritte ausgeführt werden.
