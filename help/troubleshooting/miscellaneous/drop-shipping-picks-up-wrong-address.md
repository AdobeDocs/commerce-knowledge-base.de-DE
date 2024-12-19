---
title: Der Versand nimmt die falsche Adresse an
description: Die Versandlösung erfasst nicht die Adresse der Quelle des Produkts.
exl-id: ce89713f-d506-4e4f-bf49-cdee3e6d29b5
feature: Customer Service, Orders, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---

# Der Versand nimmt die falsche Adresse an

## Problem

Die Versandlösung erfasst nicht die Adresse der Quelle des Produkts.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur (alle Versionen), mit installiertem Magento-Inventar
* Adobe Commerce On-Premises 2.3.0 und höher, mit installiertem Magento-Inventar
* Magento Open Source 2.3.0 und höher, mit installiertem Magento Inventory

### Ursache

Magento Inventory unterstützt derzeit nicht die Berechnung von Drop-Versand-Raten basierend auf der Quelladresse während des Checkouts. Stattdessen wird in allen Fällen die standardmäßige Speicheradresse aus der Konfiguration verwendet.

## Verwandtes Lesen

* [Häufig gestellte Fragen zum Magento-](https://github.com/magento/inventory/wiki/MSI-FAQs) in GitHub.
