---
title: "Adobe Commerce 2.4.0: Aktualisierung der Kundenaktivitäten nicht möglich"
description: Dieser Artikel bietet eine Lösung für das bekannte Problem mit Adobe Commerce 2.4.0, wenn ein Admin-Benutzer eine Bestellung für einen Kunden erstellt und die Aktualisierungsschaltflächen im Seitenbereich "Aktivitäten"des Kunden nicht funktionieren.
exl-id: 50048e9f-6009-4db5-ae4a-c35a84cec265
feature: Configuration
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: Aktualisierung der Kundenaktivitäten nicht möglich

Dieser Artikel bietet eine Lösung für das bekannte Problem mit Adobe Commerce 2.4.0, wenn ein Admin-Benutzer eine Bestellung für einen Kunden erstellt und die Aktualisierungsschaltflächen im Seitenbereich &quot;Aktivitäten&quot;des Kunden nicht funktionieren.

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort 2.4.0
* Adobe Commerce auf Cloud-Infrastruktur 2.4.0

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zum Bereich **Admin Panel** > **Sales** > **Bestellungen**.
1. Klicken Sie auf die Schaltfläche **Neue Bestellung erstellen** .
1. Wählen Sie den erstellten Kunden aus.
1. Markieren Sie als erstellten Kunden die Storefront.
1. Rufen Sie die Seite **Produkt** auf. Klicken Sie auf die Schaltfläche **Aktualisieren** im Abschnitt **Zuletzt angezeigte Produkte** der Aktivitäten des **Kunden**.
1. Gehen Sie zurück zur Storefront.
1. Platzieren Sie eine Bestellung mit den erstellten Produkten.
1. Gehen Sie zurück zum **Admin-Bedienfeld** und klicken Sie auf die Schaltfläche **Aktualisieren** im Abschnitt **Zuletzt bestellte Artikel** der **Aktivitäten des Kunden**.
1. Gehen Sie zurück zur Storefront. Fügen Sie das erstellte Produkt zur **Vergleichsliste** hinzu.
1. Gehen Sie zurück zum **Admin-Bedienfeld**. Klicken Sie auf die Schaltfläche **Aktualisieren** im Abschnitt **Produkte in Vergleichsliste** der Aktivitäten des **Kunden**.
1. Gehen Sie zurück zur Storefront.
1. Entfernen Sie das erstellte Produkt aus der **Vergleichsliste**.
1. Gehen Sie zurück zum **Admin-Bedienfeld**.
1. Klicken Sie auf die Schaltfläche **Aktualisieren** im Abschnitt **Zuletzt verglichene Produkte** der Aktivitäten des **Kunden**.
1. Gehen Sie zurück zur Storefront.

<u>Erwartete Ergebnisse</u>:

Der Name des Produkts sollte im Abschnitt &quot;**Zuletzt angezeigte Produkte**&quot;, &quot;**Zuletzt bestellte Artikel**&quot;, &quot;**Produkte in Vergleichsliste**&quot;und &quot;**Vor kurzem verglichene Produkte**&quot;angezeigt werden.

<u>Tatsächliche Ergebnisse</u>:

Die Seite wird jedes Mal, wenn auf die Schaltfläche **Aktualisieren** geklickt wird, nach oben gescrollt. Der Name des Produkts wird nicht im entsprechenden Abschnitt angezeigt.

## Lösung

Eine Problemumgehung besteht darin, dass der Administrator die **Aktivitäten des Kunden** aktualisieren kann, indem er unten in der Seitenleiste auf die Schaltfläche **Änderungen aktualisieren** klickt. Das Problem soll im Patch für Adobe Commerce 2.4.1 behoben werden.

![mceclip0.png](assets/mceclip0.png)

## Verwandtes Lesen

* [Bekanntes Problem in Adobe Commerce 2.4.0: Braintree-Zahlungsmethoden werden beim Checkout für mehrere Adressen nicht angezeigt](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Rohdaten werden in Storefront angezeigt](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Exportsteuersätze funktionieren nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Schaltfläche &quot;Auswahl zum Warenkorb hinzufügen&quot;funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
