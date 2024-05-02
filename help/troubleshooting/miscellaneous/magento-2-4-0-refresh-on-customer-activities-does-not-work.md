---
title: "Adobe Commerce 2.4.0: Aktualisierung der Kundenaktivitäten nicht möglich"
description: Dieser Artikel bietet eine Lösung für das bekannte Problem mit Adobe Commerce 2.4.0, wenn ein Admin-Benutzer eine Bestellung für einen Kunden erstellt und die Aktualisierungsschaltflächen im Seitenbereich "Aktivitäten"des Kunden nicht funktionieren.
exl-id: 50048e9f-6009-4db5-ae4a-c35a84cec265
feature: Configuration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: Aktualisierung der Kundenaktivitäten nicht möglich

Dieser Artikel bietet eine Lösung für das bekannte Problem mit Adobe Commerce 2.4.0, wenn ein Admin-Benutzer eine Bestellung für einen Kunden erstellt und die Aktualisierungsschaltflächen im Seitenbereich &quot;Aktivitäten&quot;des Kunden nicht funktionieren.

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort 2.4.0
* Adobe Commerce auf Cloud-Infrastruktur 2.4.0

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **Admin Panel** > **Vertrieb** > **Bestellungen**.
1. Klicken Sie auf **Neue Bestellung erstellen** Schaltfläche.
1. Wählen Sie den erstellten Kunden aus.
1. Markieren Sie als erstellten Kunden die Storefront.
1. Navigieren Sie zu **Produkt** Seite. Klicken Sie auf **Aktualisieren** Schaltfläche auf der **Kürzlich angezeigte Produkte** Abschnitt **Kundenaktivitäten**.
1. Gehen Sie zurück zur Storefront.
1. Platzieren Sie eine Bestellung mit den erstellten Produkten.
1. Gehen Sie zurück zu **Admin Panel** und klicken Sie auf **Aktualisieren** Schaltfläche des **Zuletzt sortierte Artikel** Abschnitt **Kundenaktivitäten**.
1. Gehen Sie zurück zur Storefront. Fügen Sie das erstellte Produkt zum **Vergleichsliste**.
1. Gehen Sie zurück zu **Admin Panel**. Klicken Sie auf **Aktualisieren** Schaltfläche des **Produkte in der Vergleichsliste** Abschnitt **Kundenaktivitäten**.
1. Gehen Sie zurück zur Storefront.
1. Entfernen Sie das erstellte Produkt aus der **Vergleichsliste**.
1. Gehen Sie zurück zu **Admin Panel**.
1. Klicken Sie auf **Aktualisieren** Schaltfläche des **Vor Kurzem verglichene Produkte** Abschnitt **Kundenaktivitäten**.
1. Gehen Sie zurück zur Storefront.

<u>Erwartete Ergebnisse</u>:

Der Name des Produkts sollte im **Kürzlich angezeigte Produkte**, **Zuletzt sortierte Artikel**, **Produkte in der Vergleichsliste**, und **Vor Kurzem verglichene Produkte** Abschnitt.

<u>Tatsächliche Ergebnisse</u>:

Die Seite wird jedes Mal, wenn ein **Aktualisieren** auf klicken. Der Name des Produkts wird nicht im entsprechenden Abschnitt angezeigt.

## Lösung

Eine Problemumgehung besteht darin, dass der Administrator **Kundenaktivitäten** durch Klicken auf **Änderungen aktualisieren** -Schaltfläche am unteren Rand der Seitenleiste. Das Problem soll im Patch für Adobe Commerce 2.4.1 behoben werden.

![mceclip0.png](assets/mceclip0.png)

## Verwandtes Lesen

* [Bekanntes Problem in Adobe Commerce 2.4.0: Braintree-Zahlungsmethoden werden beim Checkout für mehrere Adressen nicht angezeigt](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Bekanntes Problem bei der Erstellung von Versandbeschriftungen in Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Rohdaten werden in Storefront angezeigt](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Exportsteuersätze funktionieren nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Schaltfläche &quot;Auswahl zum Warenkorb hinzufügen&quot;funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
