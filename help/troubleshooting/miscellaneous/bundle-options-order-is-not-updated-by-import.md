---
title: Die Reihenfolge der Bundle-Optionen wird durch den Import nicht aktualisiert
description: Dieser Artikel bietet eine Lösung für das Problem, wenn nach dem Import von Produkten aus einer .csv-Datei die Paketproduktoptionen in einer anderen Reihenfolge angezeigt werden als in der Importdatei.
exl-id: 7f7bf782-4b35-4067-aa94-417097079f1f
feature: Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# Die Reihenfolge der Bundle-Optionen wird durch den Import nicht aktualisiert

Dieser Artikel bietet eine Lösung für das Problem, wenn nach dem Import von Produkten aus einer .csv-Datei die Paketproduktoptionen in einer anderen Reihenfolge angezeigt werden als in der Importdatei.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x
* Adobe Commerce lokal 2.2.x, 2.3.x
* Magento Open Source

## Problem

<u>Voraussetzungen</u>:

Sie haben eine gültige CSV-Datei, die Bundle-Produkte enthält.

<u>Zu reproduzierende Schritte</u>:

1. Importieren Sie die Datei mit der [Importfunktion](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/import/data-import).
1. Öffnen Sie die Paket-Produktseite.

<u>Erwartete Ergebnisse</u>:

Die Optionsreihenfolge entspricht der in der .csv-Datei.

<u>Tatsächliche Ergebnisse</u>:

Die Optionsreihenfolge unterscheidet sich von der in der .csv-Datei.

## Ursache

Die Position der Optionen wurde nicht explizit deklariert.

## Lösung

1. Deklarieren Sie eine Position explizit für jede Option im Parameter `position` der Spalte `bundle_values` in der CSV-Datei. Detaillierte Anweisungen finden Sie unter [Bearbeiten der Produktdaten](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/examples/data-transfer-bundle-products#method-2-edit-the-product-data) in unserem Benutzerhandbuch.
1. Wiederholen Sie den Importvorgang.

Allgemeine Informationen zum Import finden Sie im Benutzerhandbuch unter [Importieren von Bundle-Produkten](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/examples/data-transfer-bundle-products) .
