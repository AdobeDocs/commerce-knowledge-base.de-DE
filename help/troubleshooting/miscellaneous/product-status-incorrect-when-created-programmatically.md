---
title: Der Produktstatus ist bei der programmgesteuerten Erstellung falsch
description: Dieser Artikel enthält eine Korrektur für den Fall, dass der Produktstatus deaktiviert ist und Produkte nicht auf der Storefront angezeigt werden oder den falschen Store-Ansichten zugewiesen werden, wenn sie programmgesteuert erstellt/aktualisiert werden.
exl-id: ac02f961-f9e2-4620-839f-b8dbd0befb15
feature: Products
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# Der Produktstatus ist bei der programmgesteuerten Erstellung falsch

Dieser Artikel enthält eine Korrektur für den Fall, dass der Produktstatus deaktiviert ist und Produkte nicht auf der Storefront angezeigt werden oder den falschen Store-Ansichten zugewiesen werden, wenn sie programmgesteuert erstellt/aktualisiert werden.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.X.X
* Adobe Commerce On-Premise 2.X.X

## Problem

Wenn die Katalogprodukte programmgesteuert von einem Skript erstellt oder aktualisiert werden, bei dem die Adobe Commerce-Anwendung bootstrapping unterliegt, haben Produkte möglicherweise den Status Deaktiviert und/oder den falschen Store-Ansichten zugewiesen.

## Ursache

Das Problem tritt möglicherweise aufgrund von ACL-Einschränkungen auf, die für die Admin-Rollen der Adobe Commerce-Instanz festgelegt wurden. Bei Bootstrapping-Anwendungen gibt es keine initialisierten Admin-Sitzungen mit entsprechenden ACL-Einstellungen. Dadurch schlagen Überprüfungen im `Magento_AdminGws` -Modul, das für die Berechtigungsprüfung bei solchen Aktionen verantwortlich ist.

## Lösung für falschen Produktstatus

Festlegen einer dynamischen ID-Voreinstellung für die `Magento\Framework\Authorization\PolicyInterface`, wie im Abschnitt [ObjectManager > Programmatische Produktaktualisierungen](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/object-manager.html#programmatic-product-updates) Thema in unserer Entwicklerdokumentation.

## Verwandtes Lesen

* [GitHub: Der Produktstatus kann nicht geändert werden, welches Produkt mit productRepository erstellt wurde.](https://github.com/magento/magento2/issues/5664)
