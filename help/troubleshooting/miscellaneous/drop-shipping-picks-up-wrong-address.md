---
title: Ablegen des Versands nimmt falsche Adresse auf
description: Die Versandlösung nimmt die Adresse der Produktquelle nicht auf.
exl-id: ce89713f-d506-4e4f-bf49-cdee3e6d29b5
feature: Customer Service, Orders, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---

# Ablegen des Versands nimmt falsche Adresse auf

## Problem

Die Versandlösung nimmt die Adresse der Produktquelle nicht auf.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur (alle Versionen) mit installiertem Magento-Inventar
* Adobe Commerce On-Premise 2.3.0 und höher, mit installiertem Magento Inventory
* Magento Open Source 2.3.0 und höher mit installiertem Magento Inventory

### Ursache

Magento Inventory unterstützt derzeit nicht die Verwendung der Berechnung von Drops-Versandraten basierend auf der Quelladresse während des Checkouts. Stattdessen wird in allen Fällen die standardmäßige Speicheradresse aus der Konfiguration verwendet.

## Verwandte Informationen

* [Magento Inventar-FAQ](https://github.com/magento/inventory/wiki/MSI-FAQs) in GitHub.
