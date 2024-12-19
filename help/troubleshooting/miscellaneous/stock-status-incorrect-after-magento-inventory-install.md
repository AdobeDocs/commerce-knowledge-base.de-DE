---
title: Lagerstatus nach Inventory management-Installation falsch
description: Dieser Artikel enthält eine Fehlerbehebung für den Fall, dass der Lagerstatus nach der Installation/dem Upgrade von Inventory management falsch ist.
exl-id: ae32fbe3-deab-4f31-b427-95f8b54a476f
feature: Install, Inventory, Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# Lagerstatus nach Inventory management-Installation falsch

Dieser Artikel enthält eine Fehlerbehebung für den Fall, dass der Lagerstatus nach der Installation/dem Upgrade von Inventory management falsch ist.

## Lagerstatus auf einigen Sites falsch

Nach der ersten Installation oder dem Upgrade auf Inventory management in der Adobe Commerce-Umgebung mit mehreren Websites verfügen nicht alle Websites über den richtigen Lagerstatus für -Produkte.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, alle Versionen, mit installiertem Inventory management
* Adobe Commerce On-Premises 2.3.0 und höher, mit installiertem Inventory management
* Magento Open Source 2.3.0 und höher, mit installiertem Inventory management

## Ursache

Bei der ersten Installation/Aktualisierung werden alle Produkte der Standardquelle zugewiesen, sodass alle Mengen mit dieser Quelle verknüpft werden. Die Standard-Source wird dem Standard-Stock zugewiesen, wobei die Standard-Website mit der Standard-Website verknüpft ist.

## Lösung

Wenn Sie über mehr als eine Website verfügen, müssen Sie diese Websites als Sales Channel zum Standardbestand oder zu anderen benutzerdefinierten Stocks hinzufügen.

Weitere Informationen dazu [ Sie im Abschnitt „Stock“ ](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/stocks/stocks-manage) Wiki/Benutzerhandbuch in unserem Benutzerhandbuch.
