---
title: '"Adobe Commerce 2.4.0: "Auswahl zu meinem Warenkorb hinzufügen"funktioniert nicht.'
description: Dieser Artikel bietet eine Problemumgehung für ein defektes Schaltflächenkartell, das im Commerce-Administrator bei der Verwaltung des Warenkorbs eines Kunden bekannt ist. Beim Versuch, ausgewählte Produkte zum Warenkorb eines Kunden hinzuzufügen, funktioniert die Schaltfläche **Auswahl zu meinem Warenkorb hinzufügen** unten im Abschnitt nicht. Dieses Problem tritt auf jeder Seite des Admin-Bedienfelds auf, die zwei Schaltflächen **Auswahl zu meinem Warenkorb hinzufügen** enthält. In Adobe Commerce 2.4.1 wird eine permanente Korrektur verfügbar sein.
exl-id: b0830ec2-2aea-4afb-8d02-e9c8f54283be
feature: Orders, Shopping Cart
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: &quot;Auswahl zum Warenkorb hinzufügen&quot;funktioniert nicht

Dieser Artikel bietet eine Problemumgehung für ein defektes Schaltflächenkartell, das im Commerce-Administrator bei der Verwaltung des Warenkorbs eines Kunden bekannt ist. Wenn Sie versuchen, ausgewählte Produkte zum Warenkorb eines Kunden hinzuzufügen, wird die **Auswahlen zum Warenkorb hinzufügen** -Schaltfläche unten im Abschnitt funktioniert nicht. Dieses Problem tritt auf jeder Seite des Admin-Bereichs auf, die zwei **Auswahlen zum Warenkorb hinzufügen** Schaltflächen. In Adobe Commerce 2.4.1 wird eine permanente Korrektur verfügbar sein.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.4.0 (alle Bereitstellungsmethoden)

## Problem

<u>Zu reproduzierende Schritte</u>

1. Navigieren Sie zu einer beliebigen Admin Panel-Seite, die zwei enthält. **Auswahlen zum Warenkorb hinzufügen** Schaltflächen.
1. Wählen Sie Artikel aus, die zum Warenkorb hinzugefügt werden sollen.
1. Klicken Sie auf **Auswahlen zum Warenkorb hinzufügen** -Schaltfläche am unteren Rand des Bereichs.

<u>Erwartetes Ergebnis</u>

Alle Auswahlen werden wie erwartet zum Warenkorb hinzugefügt.

<u>Tatsächliches Ergebnis</u>

Adobe Commerce fügt Ihre Auswahl nicht zu meinem Warenkorb hinzu.

## Lösung

Die **Auswahlen zum Warenkorb hinzufügen** -Schaltfläche am oberen Rand der Seite funktioniert weiterhin. Das Problem wird voraussichtlich in Adobe Commerce-Version 2.4.1 behoben, die für die Veröffentlichung in Q4 1 geplant ist.

## Verwandtes Lesen

* [Verwalten eines Warenkorbs durch MerchDocs](https://docs.magento.com/user-guide/sales/shopping-assisted-cart-manage.html) in unserem Benutzerhandbuch.
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Rohdaten werden in Storefront angezeigt](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md) in unserer Wissensdatenbank.
* [Bekanntes Problem in Adobe Commerce 2.4.0: Exportsteuersätze funktionieren nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md) in unserer Wissensdatenbank.
* [Bekanntes Problem in Adobe Commerce 2.4.0: Braintree-Zahlungsmethoden werden beim Checkout für mehrere Adressen nicht angezeigt](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md) in unserer Wissensdatenbank.
