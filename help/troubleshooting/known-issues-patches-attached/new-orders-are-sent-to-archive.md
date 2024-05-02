---
title: Neue Bestellungen werden archiviert
description: Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce 2.2.0-Problem im Zusammenhang mit den neu erstellten Bestellungen, die im Archiv angezeigt werden, anstelle des Orders-Rasters in der Commerce Admin.
exl-id: 37b70d28-0569-44f2-b677-29b2bde0bc5c
feature: Storage, Data Import/Export
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# Neue Bestellungen werden archiviert

Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce 2.2.0-Problem im Zusammenhang mit den neu erstellten Bestellungen, die im Archiv angezeigt werden, anstelle des Orders-Rasters in der Commerce Admin.

>[!NOTE]
>
>Das Problem wurde in Version 2.2.3 und höher behoben.

## Problem

Wenn Kunden Bestellungen aufgeben, werden sie im archivierten Bestellungsraster anstelle des Rasters für reguläre Bestellungen angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Fügen Sie ein Produkt zum Warenkorb in der Storefront hinzu, fahren Sie mit dem Checkout fort und platzieren Sie die Bestellung.
1. Navigieren Sie in Commerce Admin zu **Vertrieb** > **Aktivitäten** > **Bestellung**. Die Reihenfolge wird im Raster angezeigt.
1. Navigieren Sie zu **Vertrieb** > **Archivieren** > **Bestellungen**. Die neue Reihenfolge wird im Raster angezeigt.

<u>Erwartete Ergebnisse</u>:

Die Reihenfolge wird nur im Raster Bestellungen angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Die Reihenfolge wird im Raster Bestellungen und im Archivraster der Bestellung angezeigt.

## Lösung

Nach dem Anwenden des Patches werden Bestellungen wie erwartet im Bestellraster angezeigt. Sie müssen jedoch im Commerce-Admin die Elemente manuell wiederherstellen, die zum Archivieren gesendet wurden, bevor der Patch angewendet wurde.

## Patch

Der Patch ist an diesen Artikel angehängt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[MDVA-8007\_EE\_2.2.0\_v1.composer.patch herunterladen](assets/MDVA-8007_EE_2.2.0_v1.composer.patch.zip)

### Kompatible Adobe Commerce-Versionen:

Der Patch wurde für erstellt:

* Adobe Commerce 2.2.0

Der Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):

* Adobe Commerce vor Ort, Adobe Commerce über Cloud-Infrastruktur 2.2.1 - 2.2.3

## Anwenden des Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe Commerce bereitgestellten Komponentenpatches](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in unserer Wissensdatenbank.

## Nützliche Links in unserem Benutzerhandbuch

* [Verwalten archivierter Bestellungen](https://docs.magento.com/user-guide/sales/order-archive.html)

## Attached Files
