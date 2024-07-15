---
title: Der Lagerstatus ist nach Inventory management-Installation falsch
description: Dieser Artikel enthält eine Fehlerbehebung für den falschen Lagerstatus nach der Installation/Aktualisierung von Inventory management.
exl-id: ae32fbe3-deab-4f31-b427-95f8b54a476f
feature: Install, Inventory, Orders
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# Der Lagerstatus ist nach Inventory management-Installation falsch

Dieser Artikel enthält eine Fehlerbehebung für den falschen Lagerstatus nach der Installation/Aktualisierung von Inventory management.

## Lagerstatus auf einigen Sites falsch

Nach der ersten Installation oder Aktualisierung, um Inventory management in der Adobe Commerce-Umgebung mit mehreren Websites zu haben, verfügen nicht alle Websites über den richtigen Lagerstatus für Produkte.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle Versionen mit installiertem Inventory management
* Adobe Commerce vor Ort 2.3.0 und höher, mit installiertem Inventory management
* Magento Open Source 2.3.0 und höher mit installiertem Inventory management

## Ursache

Bei der ersten Installation/Aktualisierung werden alle Ihre Produkte der Standardquelle zugeordnet, wobei alle Mengen dieser Quelle zugeordnet werden. Der Standard-Source wird dem Standardbestand zugewiesen, wobei die Standard-Website mit zugeordnet ist.

## Lösung

Wenn Sie mehr als eine Website haben, müssen Sie diese Websites als Sales Channel zum Standardbestand oder anderen benutzerdefinierten Lagern hinzufügen.

Weitere Informationen dazu finden Sie im Abschnitt [Stock des Wiki/Benutzerhandbuchs](https://docs.magento.com/m2/ce/user_guide/catalog/inventory-stock.html) in unserem Benutzerhandbuch.
