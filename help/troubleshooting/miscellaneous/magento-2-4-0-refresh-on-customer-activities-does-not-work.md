---
title: 'Adobe Commerce 2.4.0: Aktualisierung der Aktivitäten des Kunden funktioniert nicht'
description: Dieser Artikel bietet eine Lösung für ein bekanntes Problem in Adobe Commerce 2.4.0, wenn ein Admin-Benutzer eine Bestellung für einen Kunden erstellt und die Schaltflächen zum Aktualisieren im seitlichen Bedienfeld „Aktivitäten“ des Kunden nicht funktionieren.
exl-id: 50048e9f-6009-4db5-ae4a-c35a84cec265
feature: Configuration
role: Developer
source-git-commit: 9cd9720a73b8ecde3baf6a7a5b5732ad1330feee
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: Aktualisierung der Aktivitäten des Kunden funktioniert nicht

Dieser Artikel bietet eine Lösung für ein bekanntes Problem in Adobe Commerce 2.4.0, wenn ein Admin-Benutzer eine Bestellung für einen Kunden erstellt und die Schaltflächen zum Aktualisieren im seitlichen Bedienfeld „Aktivitäten“ des Kunden nicht funktionieren.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises 2.4.0
* Adobe Commerce auf Cloud-Infrastruktur 2.4.0

## Problem

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **Admin-Bedienfeld** > **Verkauf** > **Bestellungen**.
1. Klicken Sie auf **Schaltfläche „Neuen Auftrag erstellen**.
1. Wählen Sie den erstellten Kunden aus.
1. Gehen Sie als erstellter Kunde zur Storefront.
1. Navigieren Sie zur Seite **Produkt**. Klicken Sie auf **Aktualisieren** im Abschnitt **Kürzlich angezeigte Produkte** der **Kundenaktivitäten**.
1. Geh zurück zum Laden.
1. Bestellung mit den erstellten Produkten aufgeben.
1. Gehen Sie zurück zum **Admin** und klicken Sie auf die Schaltfläche **Aktualisieren** im Abschnitt **Letzte bestellte Artikel** der **Kundenaktivitäten**.
1. Geh zurück zum Laden. Fügen Sie das erstellte Produkt zur **Vergleichsliste“**.
1. Kehren Sie zum **Admin-Bedienfeld“**. Klicken Sie auf **Schaltfläche** Aktualisieren“ im Abschnitt **Produkte in**) von **Kundenaktivitäten**.
1. Geh zurück zum Laden.
1. Entfernen Sie das erstellte Produkt aus der **Vergleichsliste**.
1. Kehren Sie zum **Admin-Bedienfeld“**.
1. Klicken Sie auf **Aktualisieren** im Abschnitt **Kürzlich verglichene Produkte** von **Kundenaktivitäten**.
1. Geh zurück zum Laden.

<u>Erwartete Ergebnisse</u>:

Der Name des Produkts sollte im Abschnitt **Kürzlich angezeigte Produkte**, **Zuletzt bestellte Artikel**, **Produkte in der Vergleichsliste** und **Kürzlich vergleichbare Produkte** angezeigt werden.

<u>Tatsächliche Ergebnisse</u>:

Die Seite wird jedes Mal nach oben gescrollt, wenn **Schaltfläche** Aktualisieren“ angeklickt wird. Der Name des Produkts wird nicht im entsprechenden Abschnitt angezeigt.

## Lösung

Eine Problemumgehung besteht darin, dass der Admin **Benutzer bzw. die Admin-Benutzerin die** Aktivitäten des Kunden) aktualisieren kann, indem er bzw. sie unten in der Seitenleiste auf **Änderungen aktualisieren** klickt. Das Problem soll mit dem Patch für Adobe Commerce 2.4.1 behoben werden.

![mceclip0.png](assets/mceclip0.png)

## Verwandtes Lesen

* [Adobe Commerce 2.4.0 Bekanntes Problem: Braintree-Zahlungsmethoden werden beim Checkout für mehrere Adressen nicht angezeigt](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0 Bekanntes Problem: Exportsteuersätze funktionieren nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Die Schaltfläche „Auswahl zu meinem Warenkorb hinzufügen“ funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
