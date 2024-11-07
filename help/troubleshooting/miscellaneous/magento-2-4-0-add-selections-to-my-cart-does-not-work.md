---
title: '"Adobe Commerce 2.4.0: "Auswahl zu meinem Warenkorb hinzufügen"funktioniert nicht.'
description: Dieser Artikel bietet eine Problemumgehung für ein defektes Schaltflächenkartell, das im Commerce-Administrator bei der Verwaltung des Warenkorbs eines Kunden bekannt ist. Beim Versuch, ausgewählte Produkte zum Warenkorb eines Kunden hinzuzufügen, funktioniert die Schaltfläche **Auswahl zu meinem Warenkorb hinzufügen** unten im Abschnitt nicht. Dieses Problem tritt auf jeder Seite des Admin-Bedienfelds auf, die zwei Schaltflächen **Auswahl zu meinem Warenkorb hinzufügen** enthält. In Adobe Commerce 2.4.1 wird eine permanente Korrektur verfügbar sein.
exl-id: b0830ec2-2aea-4afb-8d02-e9c8f54283be
feature: Orders, Shopping Cart
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: &quot;Auswahl zum Warenkorb hinzufügen&quot;funktioniert nicht

Dieser Artikel bietet eine Problemumgehung für ein defektes Schaltflächenkartell, das im Commerce-Administrator bei der Verwaltung des Warenkorbs eines Kunden bekannt ist. Beim Versuch, ausgewählte Produkte zum Warenkorb eines Kunden hinzuzufügen, funktioniert die Schaltfläche **Auswahl zum Warenkorb hinzufügen** unten im Abschnitt nicht. Dieses Problem tritt auf jeder Seite des Admin-Bedienfelds auf, die zwei Schaltflächen &quot;**Auswahl zu meinem Warenkorb hinzufügen**&quot;enthält. In Adobe Commerce 2.4.1 wird eine permanente Korrektur verfügbar sein.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.4.0 (alle Bereitstellungsmethoden)

## Problem

<u>Zu reproduzierende Schritte</u>

1. Navigieren Sie zu einer beliebigen Admin-Bedienfeldseite, die zwei Schaltflächen **Auswahl zu meinem Warenkorb hinzufügen** enthält.
1. Wählen Sie Artikel aus, die zum Warenkorb hinzugefügt werden sollen.
1. Klicken Sie unten im Bereich auf die Schaltfläche **Auswahl zu meinem Warenkorb hinzufügen** .

<u>Erwartetes Ergebnis</u>

Alle Auswahlen werden wie erwartet zum Warenkorb hinzugefügt.

<u>Tatsächliches Ergebnis</u>

Adobe Commerce fügt Ihre Auswahl nicht zu meinem Warenkorb hinzu.

## Lösung

Die Schaltfläche **Auswahl zu meinem Warenkorb hinzufügen** oben auf der Seite funktioniert weiterhin. Das Problem wird voraussichtlich in Adobe Commerce-Version 2.4.1 behoben, die für die Veröffentlichung in Q4 1 geplant ist.

## Verwandtes Lesen

* [Verwalten eines Warenkorbs durch MerchDocs](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/assist/shopping-assisted-cart-manage) in unserem Benutzerhandbuch.
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Rohdaten von Nachrichten werden in der Storefront](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md) in unserer Support-Wissensdatenbank angezeigt.
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Exportsteuersätze funktionieren nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md) in unserer Support-Wissensdatenbank.
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Braintree-Zahlungsmethoden werden in unserer Support-Wissensdatenbank nicht beim Checkout mit mehreren Adressen angezeigt](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md).
