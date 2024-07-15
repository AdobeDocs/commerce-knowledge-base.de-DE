---
title: Bestellungen werden nicht im Raster Bestellungen in der Admin-Konsole angezeigt
description: Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce 2.2.1-Problem, das sich auf die Bestellungen bezieht, die nicht im Raster Bestellungen in Commerce Admin angezeigt werden.
exl-id: b8376760-6558-41ed-8c6b-51c5759e831a
feature: Admin Workspace, B2B, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# Bestellungen werden nicht im Raster Bestellungen in der Admin-Konsole angezeigt

Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce 2.2.1-Problem, das sich auf die Bestellungen bezieht, die nicht im Raster Bestellungen in Commerce Admin angezeigt werden.

## Problem

In Adobe Commerce 2.2.1 mit installierter B2B-Erweiterung werden Bestellungen, die von einem registrierten Kunden auf der Storefront erstellt wurden, nicht in der Liste der Bestellungen im Kundenkonto im Commerce Admin angezeigt. Im Debug-Protokoll (`./var/log/debug.log`) wird der folgende Fehler protokolliert:

`report.CRITICAL: You cannot define a correlation name ‘company_order’ more than once`

<u>Voraussetzungen</u>:

Ihr Store-Katalog enthält Produkte, nicht Adobe Commerce-Beispieldaten, und die B2B-Erweiterung wird installiert.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zur Storefront und erstellen Sie ein Kundenkonto.
1. Fügen Sie ein Produkt zum Warenkorb hinzu, schließen Sie den Checkout ab und senden Sie eine Bestellung.
1. Melden Sie sich beim Administrator an.
1. Navigieren Sie zu **Kunden,** und wählen Sie dann **Alle Kunden** aus.
1. Klicken Sie für den neu erstellten Kunden auf **Bearbeiten**.
1. Klicken Sie im Bereich auf der linken Seite auf **Bestellungen** .

<u>Erwartetes Ergebnis</u>:

Die kürzlich gesendete Bestellung wird im Raster aufgeführt.

<u>Tatsächliches Ergebnis</u>:

Das Raster Bestellungen wird nicht angezeigt. Stattdessen wird eine leere Seite angezeigt.

## Patch

Der Patch ist an diesen Artikel angehängt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[MDVA-7868\_EE\_2.2.1\_v1\_composer.patch herunterladen](assets/MDVA-7868_EE_2.2.1_v1_composer.patch.zip)

### Kompatible Adobe Commerce-Versionen:

Der Patch wurde für erstellt:

* Adobe Commerce vor Ort 2.2.1

Der Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):

* Adobe Commerce für Cloud-Infrastruktur von 2.2.0 bis 2.2.3
* Adobe Commerce vor Ort 2.2.0 und 2.2.2 bis 2.2.3

## Anwenden des Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches in unserer Support-Wissensdatenbank.

## Attached Files
