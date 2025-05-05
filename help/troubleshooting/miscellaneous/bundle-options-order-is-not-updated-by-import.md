---
title: Reihenfolge der Bundle-Optionen wird beim Import nicht aktualisiert
description: Dieser Artikel bietet eine Lösung für das Problem, dass nach dem Importieren von Produkten aus einer CSV-Datei die Bundle-Produktoptionen in einer anderen Reihenfolge angezeigt werden als in der Importdatei aufgeführt.
exl-id: 7f7bf782-4b35-4067-aa94-417097079f1f
feature: Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# Reihenfolge der Bundle-Optionen wird beim Import nicht aktualisiert

Dieser Artikel bietet eine Lösung für das Problem, dass nach dem Importieren von Produkten aus einer CSV-Datei die Bundle-Produktoptionen in einer anderen Reihenfolge angezeigt werden als in der Importdatei aufgeführt.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x
* Adobe Commerce On-Premises 2.2.x, 2.3.x
* Magento Open Source

## Problem

<u>Voraussetzungen</u>:

Sie haben eine gültige CSV-Datei, die Bundle-Produkte enthält.

<u>Schritte zur Reproduktion</u>:

1. Importieren Sie die Datei mit der [Importfunktion](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/data-transfer/import/data-import).
1. Öffnen Sie die Bundle-Produktseite.

<u>Erwartete Ergebnisse</u>:

Die Reihenfolge der Optionen entspricht der in der CSV-Datei.

<u>Tatsächliche Ergebnisse</u>:

Die Reihenfolge der Optionen unterscheidet sich von der in der CSV-Datei.

## Ursache

Die Optionsposition wurde nicht explizit deklariert.

## Lösung

1. Deklarieren Sie explizit eine Position für jede Option im `position` der Spalte `bundle_values` in der CSV-Datei. Detaillierte Anweisungen finden Sie [Bearbeiten der Produktdaten](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/data-transfer/examples/data-transfer-bundle-products#method-2-edit-the-product-data) in unserem Benutzerhandbuch.
1. Wiederholen Sie den Importvorgang.

Allgemeine Informationen zum Importieren finden Sie unter [Importieren von Bundle-](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/data-transfer/examples/data-transfer-bundle-products)) in unserem Benutzerhandbuch.
