---
title: 'Bekanntes Problem mit Adobe Commerce 2.3.5: Multi-Ship-Bestellungen für virtuelle Produkte'
description: In diesem Artikel wird ein bekanntes Problem in Adobe Commerce 2.3.5 erläutert, bei dem eine Multi-Shipping-Bestellung mit einem virtuellen Produkt nicht korrekt verarbeitet wird.
exl-id: 34ce79a2-5157-492b-8ee4-bdc09aae0c40
feature: Orders, Products, Shipping/Delivery
role: Developer
source-git-commit: 39e61a3fe8b75fb613819d89c7d47acdf1c384f6
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---

# Bekanntes Problem mit Adobe Commerce 2.3.5: Multi-Ship-Bestellungen für virtuelle Produkte

In diesem Artikel wird ein bekanntes Problem in Adobe Commerce 2.3.5 erläutert, bei dem eine Multi-Shipping-Bestellung mit einem virtuellen Produkt nicht korrekt verarbeitet wird.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises 2.3.5
* Adobe Commerce auf Cloud-Infrastruktur 2.3.5

## Problem

<u>Schritte zur Reproduktion</u>:

1. Fügen Sie in der Storefront physische und virtuelle Produkte zum Warenkorb hinzu.
1. Gehen Sie zum Auschecken und wählen Sie **Mit mehreren Adressen auschecken** aus.
1. Fügen Sie alle erforderlichen Informationen hinzu und geben Sie die Bestellung auf.

<u>Erwartetes Ergebnis</u>:

Bestellungen werden für alle Produkte erfolgreich aufgegeben.

<u>Tatsächliches </u>:

Die Bestellung für das virtuelle Produkt ist leer.

## Fehlerbehebung

Eine Fehlerbehebung wird in Adobe Commerce 2.3.6 verfügbar sein, die im 4. Quartal 2020 veröffentlicht werden soll.

## Verwandtes Lesen

In unserer Entwicklerdokumentation:

* Versionshinweise zu [Adobe Commerce 2.3.5](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
