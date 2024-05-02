---
title: Quelle kann nicht gelöscht oder Code geändert werden
description: Dieser Artikel enthält eine Korrektur für den Fall, dass Sie eine Quelle nicht vollständig entfernen und/oder ihren Code ändern können.
exl-id: dbdb4d62-9138-4a3d-a58f-8671f1dc5b42
feature: Console
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Quelle kann nicht gelöscht oder Code geändert werden

Dieser Artikel enthält eine Korrektur für den Fall, dass Sie eine Quelle nicht vollständig entfernen und/oder ihren Code ändern können.

## Problem

Quellen können unabhängig von der Produktzuweisung nicht gelöscht werden.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur (alle Versionen) mit installiertem Magento-Inventar
* Adobe Commerce On-Premise 2.3.0 und höher, mit installiertem Magento Inventory
* Magento Open Source 2.3.0 und höher mit installiertem Magento Inventory

## Ursache

Es ist nicht möglich, eine Quelle vollständig zu entfernen und/oder ihren Code zu ändern.

Das vollständige Entfernen einer Quelle würde zu Auftragsdatenproblemen führen, da Quellen Teil von Produktbeständen, Bestellungen, Versanddaten und vielem mehr sind.

Der Code ist für die Verbindung der Quelle mit Bestellungen von entscheidender Bedeutung. Dies ist eine eindeutige ID für die Quelle und ist für die Bearbeitung deaktiviert.

## Lösung

Sie können eine Quelle aus einem Produkt entfernen, indem Sie den Bestand übertragen oder das Produkt von allen Sendungen an einem Ort ablegen.

Wenn Sie eine Quelle aus [SSA](https://devdocs.magento.com/guides/v2.3/inventory/source-selection-algorithms.html) Berechnungen und der Verarbeitung der Lagerbestandsbestellung in Adobe Commerce können Sie die Quelle deaktivieren. Deaktivierte Quellen behalten alle Daten, zugewiesenen Produkte und Lagerbestandsmengen bei und können jederzeit wieder aktiviert werden, um den Versand wieder zu starten.

Siehe [Anleitung zum Erstellen von Quellen](https://github.com/magento/inventory/wiki/Create-Sources#disable-sources) für Details zur Deaktivierung einer Quelle.
