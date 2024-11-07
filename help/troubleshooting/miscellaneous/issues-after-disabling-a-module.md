---
title: Probleme nach dem Deaktivieren eines Moduls
description: Dieser Artikel bietet eine Lösung für Probleme mit Modulfunktionen, nachdem die Modulausgabe in der Commerce Admin deaktiviert wurde.
exl-id: 517f6993-f09e-4a94-8c57-175ecf9a98a8
feature: Extensions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---

# Probleme nach dem Deaktivieren eines Moduls

Dieser Artikel bietet eine Lösung für Probleme mit Modulfunktionen, nachdem die Modulausgabe in der Commerce Admin deaktiviert wurde.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.1.X oder früher
* Adobe Commerce On-Premise 2.1.X oder früher

## Problem

Wenn Sie die Modulausgabe in Commerce Admin unter **Stores** > **Einstellungen** > **Konfiguration** > ERWEITERT > **Erweitert** deaktiviert haben, treten möglicherweise Probleme im Zusammenhang mit der Modulfunktionalität auf.

## Ursache

Durch Deaktivieren einer Modulausgabe unter **Speicher** > **Einstellungen** > **Konfiguration** > ERWEITERT > **Erweitert** wird nur die Ausgabe (HTML, JS) deaktiviert, die Funktion dieses Moduls wird jedoch nicht deaktiviert.

## Lösung

Wenn Sie die Modulfunktionalität deaktivieren müssen, deaktivieren Sie das Modul, wie in der Entwicklerdokumentation unter [Module aktivieren oder deaktivieren](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/manage-modules) beschrieben.

Die Funktion zur Deaktivierung der Modulausgabe wurde ab Version 2.2.0 entfernt.
