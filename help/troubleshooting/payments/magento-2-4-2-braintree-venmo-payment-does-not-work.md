---
title: "Adobe Commerce 2.4.2: Braintree Venmo-Zahlung funktioniert nicht"
description: In diesem Artikel wird ein bekanntes Problem mit Adobe Commerce 2.4.2 beschrieben, bei dem Bestellungen nicht generiert werden, wenn während des Checkout Braintree Venmo verwendet wird. Derzeit steht keine Lösung zur Verfügung.
exl-id: 1832ab64-5024-444b-915e-473b34979a6e
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Adobe Commerce 2.4.2: Braintree Venmo-Zahlung funktioniert nicht

In diesem Artikel wird ein bekanntes Problem mit Adobe Commerce 2.4.2 beschrieben, bei dem Bestellungen nicht generiert werden, wenn während des Checkout Braintree Venmo verwendet wird. Derzeit steht keine Lösung zur Verfügung.

## Betroffene Produkte und Versionen

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

## Problem

<u>Precondition</u> :

Aktivieren Sie die Venmo-Zahlung in der Braintree-Konfiguration.

<u>Zu reproduzierende Schritte</u> :

1. Fügen Sie in der Storefront beliebige Artikel zum Warenkorb hinzu.
1. Fahren Sie mit **Checkout** fort.
1. Wählen Sie die entsprechende Versandmethode aus.
1. Wählen Sie **Venmo** als Zahlungsmethode aus.
1. Klicken Sie auf **Mit Venmo bezahlen**.
1. Klicken Sie auf **Bestellung platzieren**.

<u>Tatsächliche Ergebnisse</u>:

Die Bestellung wird nicht im Adobe Commerce-Code erstellt, nachdem der Kunde von der Venmo-App zum Store zurückgeleitet wurde, und es wird keine Fehlermeldung angezeigt. Die Reihenfolge wird in Braintree erstellt.

<u>Erwartete Ergebnisse</u>:

Die Bestellung wird in Adobe Commerce erstellt, nachdem der Kunde von der Venmo-App zurück zum Store zurückgeleitet wurde und die Bestellung wie erwartet in Braintree erstellt wurde.

## Lösung

Derzeit steht keine Lösung zur Verfügung.
