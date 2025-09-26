---
title: 'Adobe Commerce 2.4.0: „Auswahl zu meinem Warenkorb hinzufügen“ funktioniert nicht'
description: Dieser Artikel bietet eine Problemumgehung für ein bekanntes Problem mit einer beschädigten Schaltfläche in Commerce Admin bei der Verwaltung des Warenkorbs eines Kunden. Beim Versuch, ausgewählte Produkte zum Warenkorb eines Kunden hinzuzufügen, funktioniert die Schaltfläche **Auswahl zum Warenkorb hinzufügen** am unteren Rand des Abschnitts nicht. Dieses Problem tritt bei jeder Admin-Bedienfeldseite auf, die zwei Schaltflächen **Auswahl zum Warenkorb hinzufügen** enthält. In Adobe Commerce 2.4.1 ist eine dauerhafte Fehlerbehebung verfügbar.
exl-id: b0830ec2-2aea-4afb-8d02-e9c8f54283be
feature: Orders, Shopping Cart
role: Developer
source-git-commit: 9cd9720a73b8ecde3baf6a7a5b5732ad1330feee
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: „Auswahl zu meinem Warenkorb hinzufügen“ funktioniert nicht

Dieser Artikel bietet eine Problemumgehung für ein bekanntes Problem mit einer beschädigten Schaltfläche in Commerce Admin bei der Verwaltung des Warenkorbs eines Kunden. Beim Versuch, ausgewählte Produkte zum Warenkorb eines Kunden hinzuzufügen, funktioniert die Schaltfläche **Auswahl zum Warenkorb hinzufügen** am unteren Rand des Abschnitts nicht. Dieses Problem tritt bei jeder Admin-Bedienfeldseite auf, die zwei Schaltflächen **Auswahl zum Warenkorb hinzufügen** enthält. In Adobe Commerce 2.4.1 ist eine dauerhafte Fehlerbehebung verfügbar.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.4.0 (alle Bereitstellungsmethoden)

## Problem

<u>Schritte zur Reproduktion</u>

1. Navigieren Sie zu einer beliebigen Admin-Bedienfeldseite, die zwei Schaltflächen **Auswahl zum Warenkorb hinzufügen** enthält.
1. Artikel zum Hinzufügen zum Warenkorb auswählen.
1. Klicken Sie auf **Schaltfläche „Auswahl zum Warenkorb hinzufügen**, die sich am unteren Rand des Abschnitts befindet.

<u>Erwartetes Ergebnis</u>

Alle Auswahlen werden erwartungsgemäß zu meinem Warenkorb hinzugefügt.

<u>Tatsächliches Ergebnis</u>

Adobe Commerce fügt Ihre Auswahl nicht zu meinem Warenkorb hinzu.

## Lösung

Die **„Auswahl zum Warenkorb hinzufügen** oben auf der Seite funktioniert weiterhin. Das Problem wird voraussichtlich in Adobe Commerce Version 2.4.1 behoben, die im 4. Quartal 1 veröffentlicht werden soll.

## Verwandtes Lesen

* [MerchDocs&#39; Verwalten eines Warenkorbs](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/assist/shopping-assisted-cart-manage) in unserem Benutzerhandbuch.
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Exportsteuersätze funktionieren nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md) in unserer Support-Wissensdatenbank.
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Braintree-Zahlungsmethoden werden beim Checkout für mehrere Adressen nicht ](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md) unserer Support-Wissensdatenbank angezeigt.
