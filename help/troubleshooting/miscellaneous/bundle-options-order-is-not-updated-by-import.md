---
title: Die Reihenfolge der Bundle-Optionen wird durch den Import nicht aktualisiert
description: Dieser Artikel bietet eine Lösung für das Problem, wenn nach dem Import von Produkten aus einer .csv-Datei die Paketproduktoptionen in einer anderen Reihenfolge angezeigt werden als in der Importdatei.
exl-id: 7f7bf782-4b35-4067-aa94-417097079f1f
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
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

1. Importieren Sie die Datei mit der [Importfunktion](https://docs.magento.com/m2/ee/user_guide/system/data-import.html).
1. Öffnen Sie die Paket-Produktseite.

<u>Erwartete Ergebnisse</u>:

Die Optionsreihenfolge entspricht der in der .csv-Datei.

<u>Tatsächliche Ergebnisse</u>:

Die Optionsreihenfolge unterscheidet sich von der in der .csv-Datei.

## Ursache

Die Position der Optionen wurde nicht explizit deklariert.

## Lösung

1. Eine Position explizit für jede Option im `position` Parameter der `bundle_values` in der .csv -Datei. Detaillierte Anweisungen finden Sie unter [Produktdaten bearbeiten](https://docs.magento.com/m2/ee/user_guide/system/data-transfer-bundle-products.html#method-2-edit-the-product-data) in unserem Benutzerhandbuch.
1. Wiederholen Sie den Importvorgang.

Allgemeine Informationen zum Import finden Sie im Abschnitt [Bundle-Produkt importieren](https://docs.magento.com/m2/ee/user_guide/system/data-transfer-bundle-products.html) in unserem Benutzerhandbuch.
