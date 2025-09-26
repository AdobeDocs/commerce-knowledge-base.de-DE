---
title: 'Bekanntes Problem mit Adobe Commerce 2.4.0: Schaltflächen „Neue Bestellung erstellen“ fehlen'
description: Dieser Artikel bietet eine Problemumgehung für ein bekanntes Problem in Commerce Admin bei zwei fehlenden Schaltflächen auf der Seite zur Auftragserstellung. Bei der Erstellung einer neuen Bestellung für einen neuen oder bestehenden Kunden ist es nicht möglich, Produkte aus dem Katalog zur Bestellung hinzuzufügen, da die Schaltflächen **Produkte nach SKU hinzufügen** und **Produkte hinzufügen** fehlen. Dies liegt daran, dass das JS-Bundle aktiviert ist. Eine Fehlerbehebung wird in Adobe Commerce 2.4.1 verfügbar sein.
exl-id: 24ae880e-6d74-4444-9165-2744b12af81a
feature: B2B
role: Developer
source-git-commit: 9cd9720a73b8ecde3baf6a7a5b5732ad1330feee
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# Bekanntes Problem mit Adobe Commerce 2.4.0: Schaltflächen „Neue Bestellung erstellen“ fehlen

Dieser Artikel bietet eine Problemumgehung für ein bekanntes Problem in Commerce Admin bei zwei fehlenden Schaltflächen auf der Seite zur Auftragserstellung. Bei der Erstellung einer neuen Bestellung für einen neuen oder bestehenden Kunden ist es nicht möglich, Produkte aus dem Katalog zur Bestellung hinzuzufügen, da die Schaltflächen **Produkte nach SKU hinzufügen** und **Produkte hinzufügen** fehlen. Dies liegt daran, dass das JS-Bundle aktiviert ist. Eine Fehlerbehebung wird in Adobe Commerce 2.4.1 verfügbar sein.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises 2.4.0
* Adobe Commerce auf Cloud-Infrastruktur 2.4.0

## Problem

<u>Schritte zur Reproduktion</u>

1. Navigieren Sie **Kunden > Alle Kunden**.
1. Klicken Sie auf **Link** Bearbeiten“ auf einem Kunden.
1. Klicken Sie auf die **Bestellung erstellen**.

<u>Erwartetes Ergebnis</u>

Die **Produkte nach SKU hinzufügen** und **Produkte hinzufügen** werden auf der Seite **Neue Bestellung erstellen** angezeigt.

<u>Tatsächliches Ergebnis</u>

Die **Produkte nach SKU hinzufügen** und **Produkte hinzufügen** fehlen auf der Seite **Neue Bestellung erstellen**.

## Abhilfe

Die Problemumgehung besteht darin, das JS-Bundle für die Adobe Commerce-Instanz zu deaktivieren. Das Problem wird voraussichtlich in Adobe Commerce 2.4.1 behoben, das im 4. Quartal 2020 veröffentlicht werden soll.

## Verwandte Lesungen in unserer Support-Wissensdatenbank

* [Adobe Commerce 2.4.0 Bekanntes Problem: Exportsteuersätze funktionieren nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 Bekanntes Problem: Braintree-Zahlungsmethoden werden beim Checkout für mehrere Adressen nicht angezeigt](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Bekanntes Problem mit Adobe Commerce 2.4.0: Fehlermeldung bei Auswahl der lokalen Zahlungsmethode, die für einige Länder während des Checkouts angezeigt wird](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0 B2B-Admin kann kein konfigurierbares Produkt zum Angebot hinzufügen](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0 - Aktualisierung der Aktivitäten des Kunden funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Bekanntes Problem in Adobe Commerce 2.4.0: Die Schaltfläche „Auswahl zu meinem Warenkorb hinzufügen“ funktioniert nicht](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
