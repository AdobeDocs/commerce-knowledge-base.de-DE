---
title: Beim Massenlöschung in Admin wurden mehr Produkte gelöscht als initiiert
description: Dieser Artikel enthält einen Patch für den bekannten Adobe-С-Commerce in Cloud-Infrastruktur 2.2.3-Problem, der sich darauf bezieht, dass nicht ausgewählte Datensätze gelöscht werden, wenn in einem Raster in Commerce Admin eine Massenlöschung durchgeführt wird.
exl-id: 0bfdc84e-0292-4702-a20e-bdbe67c111a2
feature: Admin Workspace, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# Beim Massenlöschung in Admin wurden mehr Produkte gelöscht als initiiert

Dieser Artikel enthält einen Patch für den bekannten Adobe-С-Commerce in Cloud-Infrastruktur 2.2.3-Problem, der sich darauf bezieht, dass nicht ausgewählte Datensätze gelöscht werden, wenn in einem Raster in Commerce Admin eine Massenlöschung durchgeführt wird.

## Problem

Wenn Sie in Admin Kunden- oder Client-Datensätze auswählen, die gelöscht werden sollen, das Raster filtern und dann die Aktion **Löschen** auswählen, werden alle Datensätze gelöscht.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie im Admin zu **Katalog** > **Produkte** .
1. Wählen Sie ein Produkt oder mehrere Produkte aus.
1. Wählen Sie im Dropdown-Menü Aktionen die Option Löschen aus.

<u>Erwartete Ergebnisse</u>:

Nur ausgewählte Produkte werden gelöscht.

<u>Tatsächliche Ergebnisse</u>:

Einige andere Produkte werden ebenfalls gelöscht.

## Patch

Der Patch ist an diesen Artikel angehängt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[MDVA-10600\_EE\_2.2.3\_v1.composer.patch herunterladen](assets/MDVA-10600_EE_2.2.3_v1.composer.patch.zip)

### Kompatible Adobe Commerce-Versionen:

Der Patch wurde für erstellt:

* Adobe Commerce in Cloud-Infrastruktur 2.2.3

Der Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):

* Adobe Commerce vor Ort 2.1.8-2.1.14, 2.2.0-2.2.2 und 2.2.4-2.2.5
* Adobe Commerce auf Cloud-Infrastruktur 2.2.4-2.2.5

## Anwenden des Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches.
