---
title: Quelle kann nicht gelöscht oder Code geändert werden
description: Dieser Artikel bietet eine Korrektur für Fälle, in denen Sie eine Quelle nicht vollständig entfernen und/oder ihren Code ändern können.
exl-id: dbdb4d62-9138-4a3d-a58f-8671f1dc5b42
feature: Console
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Quelle kann nicht gelöscht oder Code geändert werden

Dieser Artikel bietet eine Korrektur für Fälle, in denen Sie eine Quelle nicht vollständig entfernen und/oder ihren Code ändern können.

## Problem

Quellen können unabhängig von der Produktzuweisung nicht gelöscht werden.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur (alle Versionen), mit installiertem Magento-Inventar
* Adobe Commerce On-Premises 2.3.0 und höher, mit installiertem Magento-Inventar
* Magento Open Source 2.3.0 und höher, mit installiertem Magento Inventory

## Ursache

Per Design ist es nicht möglich, eine Quelle vollständig zu entfernen und/oder ihren Code zu ändern.

Das vollständige Entfernen einer Quelle würde Probleme mit den Auftragsdaten verursachen, da die Quellen Teil der Produktinventare, Bestellungen, Lieferdaten und vieles mehr sind.

Der Code ist für die Verbindung der Quelle mit Bestellungen von entscheidender Bedeutung. Dies ist eine eindeutige ID für die Quelle, deren Bearbeitung deaktiviert ist.

## Lösung

Sie können eine Quelle aus einem Produkt entfernen, indem Sie das Inventar übertragen oder das Produkt aus allen Lieferungen an einem Speicherort ablegen.

Wenn Sie eine Quelle aus [SSA)-](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/basics/selection-reservations) und der Adobe Commerce-Inventarauftragsverarbeitung entfernen müssen, können Sie die Quelle deaktivieren. Deaktivierte Quellen speichern alle Daten, zugewiesenen Produkte und Lagermengen und können jederzeit wieder aktiviert werden, um den Versand wieder aufzunehmen.

Weitere Informationen zum Deaktivieren einer [ finden Sie ](https://github.com/magento/inventory/wiki/Create-Sources#disable-sources) Handbuch zum Erstellen von Quellen .
