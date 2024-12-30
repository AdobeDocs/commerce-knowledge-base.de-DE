---
title: Produktstatus bei programmatischer Erstellung falsch
description: Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass der Produktstatus deaktiviert ist und Produkte nicht in der Storefront angezeigt werden oder falschen Store-Ansichten zugewiesen werden, wenn sie programmgesteuert erstellt/aktualisiert werden.
exl-id: ac02f961-f9e2-4620-839f-b8dbd0befb15
feature: Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# Produktstatus bei programmatischer Erstellung falsch

Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass der Produktstatus deaktiviert ist und Produkte nicht in der Storefront angezeigt werden oder falschen Store-Ansichten zugewiesen werden, wenn sie programmgesteuert erstellt/aktualisiert werden.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.x.x
* Adobe Commerce On-Premises 2.X.X

## Problem

Wenn die Katalogprodukte programmgesteuert von einem Skript mit Adobe Commerce-Programm-Bootstrapping erstellt oder aktualisiert werden, haben Produkte möglicherweise den Status Deaktiviert und/oder den falschen Shop-Ansichten zugewiesen.

## Ursache

Das Problem kann aufgrund von ACL-Einschränkungen auftreten, die für die Administratorrollen der Adobe Commerce-Instanz festgelegt sind. Bei einem Bootstrapping der Anwendung gibt es keine initialisierten Admin-Sitzungen mit entsprechenden ACL-Einstellungen. Dies würde dazu führen, dass Validierungen im `Magento_AdminGws`-Modul fehlschlagen, das für die Berechtigungsprüfung für solche Aktionen verantwortlich ist.

## Lösung für falschen Produktstatus

Legen Sie eine dynamische ID-Voreinstellung für die `Magento\Framework\Authorization\PolicyInterface` fest, wie im Thema [ObjectManager>Programmatische Produktaktualisierungen](https://developer.adobe.com/commerce/php/development/components/object-manager/) in unserer Entwicklerdokumentation beschrieben.

## Verwandtes Lesen

* [GitHub: Der Produktstatus des mit productRepository erstellten Produkts kann nicht geändert werden](https://github.com/magento/magento2/issues/5664)
