---
title: Importieren von CSV-Produktinformationen für dasselbe Produkt schlägt fehl
description: Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce 2.2.3-Problem, bei dem beim Versuch, eine ".csv"-Datei mit Produktinformationen zu importieren, Fehler ausgegeben werden, wenn es Produkte mit demselben Namen gibt.
exl-id: 420b0283-455a-4bd5-ba51-18f341ddacd5
feature: Data Import/Export, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Importieren von CSV-Produktinformationen für dasselbe Produkt schlägt fehl

Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce 2.2.3-Problem im Zusammenhang mit dem Abrufen von Fehlern beim Versuch, eine `.csv` -Datei mit Produktinformationen, wenn es Produkte mit demselben Namen gibt.

## Problem

Wenn eine `.csv` -Datei mit Produktinformationen importiert wird und es Produkte mit demselben Namen gibt, erhalten Sie im Schritt Daten überprüfen den folgenden Fehler: *&quot;`URL Key XYZ was already generated for an item with the SKU %sku%"`*. Das Problem wird dadurch verursacht, dass die URLs der Produkte während des Imports umgeschrieben werden, selbst wenn in den importierten Produkten keine Spalte für die URLs enthalten ist `.csv` -Datei.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie im Commerce-Admin zwei konfigurierbare Produkte mit demselben Namen.
1. Erstellen Sie eine `.csv` -Datei, um Daten für diese Produkte zu importieren, die beispielsweise die folgenden Spalten enthalten: `sku` | `product_type` | `name` | `product_websites` | `store_view_code`
1. Navigieren Sie zu **System** > **Datenübertragung** > **Import** und wählen Sie die `.csv` -Datei.
1. Klicks **Daten überprüfen**.

<u>Erwartetes Ergebnis</u>:

Keine Probleme gefunden; Sie können die `.csv` -Datei.

<u>Tatsächliches Ergebnis</u>:

Die folgende Fehlermeldung wird angezeigt: *&quot;URL-Schlüssel XYZ wurde bereits für ein Element mit der SKU %sku% generiert.&quot;*, ist es nicht möglich, die Datei zu importieren.

## Patch

Der Patch ist an diesen Artikel angehängt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[MDVA-12899\_EE\_2.2.3\_COMPOSER\_v2.patch herunterladen](assets/MDVA-12899_EE_2.2.3_COMPOSER_v2.patch.zip)

### Kompatible Adobe Commerce-Versionen:

Der Patch wurde für erstellt:

* Adobe Commerce vor Ort 2.2.3

Der Patch ist auch mit den folgenden Adobe Commerce-Editionen und -Versionen kompatibel (löst das Problem jedoch möglicherweise nicht):

* Adobe Commerce für Cloud-Infrastruktur von 2.2.0 bis 2.2.7 und 2.3.0
* Adobe Commerce vor Ort von 2.2.0 bis 2.2.2, von 2.2.4 bis 2.2.7 und 2.3.0

## Anwenden des Pflasters

Siehe [Anwenden eines von Adobe Commerce bereitgestellten Komponentenpatches](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in unserer Support-Wissensdatenbank für Anleitungen.

## Nützliche Links

[Anwenden benutzerdefinierter Patches auf Adobe Commerce in der Cloud-Infrastruktur](https://devdocs.magento.com/guides/v2.3/cloud/project/project-patch.html)

## Attached Files
