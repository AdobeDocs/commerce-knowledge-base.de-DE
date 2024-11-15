---
title: Bekanntes Problem bei der Produktanzahl für Massenaktionen in Adobe Commerce 2.3.5
description: In diesem Artikel wird ein bekanntes Adobe Commerce 2.3.5-Problem beschrieben, bei dem die Benachrichtigung, die ein Händler nach einer Massenaktion in Admin erhält, eine falsche Anzahl von betroffenen Elementen enthält.
exl-id: 3ede15d4-4c39-442a-8784-2d5e6650fe67
feature: Products
role: Developer
source-git-commit: b3d39e6b02728f05f046adf7be94ffacbca944d5
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---

# Bekanntes Problem bei der Produktanzahl für Massenaktionen in Adobe Commerce 2.3.5

In diesem Artikel wird ein bekanntes Adobe Commerce 2.3.5-Problem beschrieben, bei dem die Benachrichtigung, die ein Händler nach einer Massenaktion in Admin erhält, eine falsche Anzahl von betroffenen Elementen enthält.

## Betroffene Produkte und Versionen

* Adobe Commerce in Cloud-Infrastruktur 2.3.5
* Adobe Commerce vor Ort 2.3.5

## Problem

Die von Adobe Commerce nach einer Massenaktion angezeigte Systemmeldung (z. B. ein Massenprodukt-Update oder Import/Export) zeigt die Anzahl der Produkte mit 0 anstelle der genauen Anzahl der Produkte an, die von der Massenaktion betroffen sind.

## Fehlerbehebung

In Adobe Commerce 2.3.6, das ab 4. Quartal 2020 veröffentlicht werden soll, ist eine Korrektur verfügbar.

## Verwandtes Lesen

* Knowledge Base-Artikel zur Adobe Commerce-Unterstützung für bekannte Probleme mit Adobe Commerce 2.3.5:
   * [Multi-Versandaufträge mit einem virtuellen Produkt werden in Adobe Commerce 2.3.5 nicht korrekt verarbeitet](/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md)
   * [Bekanntes Problem beim Produktvergleich in Adobe Commerce 2.3.5](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)
   * [Patch für Amazon Pay-out-Problem in Adobe Commerce 2.3.5-p1](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)
   * [Bekannte Probleme mit Adobe Commerce 2.3.5 in unserer Entwicklerdokumentation](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
