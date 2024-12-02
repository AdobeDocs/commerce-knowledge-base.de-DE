---
title: 'Bekanntes Problem mit Adobe Commerce 2.3.5: Multi-ship-Bestellungen für virtuelle Produkte'
description: In diesem Artikel wird ein bekanntes Problem in Adobe Commerce 2.3.5 erläutert, bei dem eine Bestellung mit mehreren Sendungen, die ein virtuelles Produkt enthalten, nicht ordnungsgemäß verarbeitet wird.
exl-id: 34ce79a2-5157-492b-8ee4-bdc09aae0c40
feature: Orders, Products, Shipping/Delivery
role: Developer
source-git-commit: b3d39e6b02728f05f046adf7be94ffacbca944d5
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Bekanntes Problem mit Adobe Commerce 2.3.5: Multi-ship-Bestellungen für virtuelle Produkte

In diesem Artikel wird ein bekanntes Problem in Adobe Commerce 2.3.5 erläutert, bei dem eine Bestellung mit mehreren Sendungen, die ein virtuelles Produkt enthalten, nicht ordnungsgemäß verarbeitet wird.

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort 2.3.5
* Adobe Commerce in Cloud-Infrastruktur 2.3.5

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Fügen Sie dem Warenkorb physische und virtuelle Produkte hinzu.
1. Fahren Sie mit dem Checkout fort und wählen Sie **Mit mehreren Adressen auschecken** aus.
1. Fügen Sie alle erforderlichen Informationen hinzu und geben Sie die Bestellung auf.

<u>Erwartetes Ergebnis</u>:

Bestellungen werden für alle Produkte erfolgreich platziert.

<u>Tatsächliches Ergebnis</u>:

Die Reihenfolge für das virtuelle Produkt ist leer.

## Fehlerbehebung

In Adobe Commerce 2.3.6, das ab 4. Quartal 2020 veröffentlicht werden soll, ist eine Korrektur verfügbar.

## Verwandtes Lesen

In unserer Support-Wissensdatenbank:

* [Bekanntes Problem beim Produktvergleich in Adobe Commerce 2.3.5](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)
* [Bekanntes Problem bei der Produktanzahl für Massenaktionen in Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)
* [Patch für Amazon Pay-out-Problem in Adobe Commerce 2.3.5-p1](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)

In unserer Entwicklerdokumentation:

* [Adobe Commerce 2.3.5 - Versionshinweise](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
