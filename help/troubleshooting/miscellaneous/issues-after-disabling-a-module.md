---
title: Probleme nach der Deaktivierung eines Moduls
description: Dieser Artikel bietet eine Lösung für Probleme mit der Modulfunktionalität, nachdem die Modulausgabe in Commerce Admin deaktiviert wurde.
exl-id: 517f6993-f09e-4a94-8c57-175ecf9a98a8
feature: Extensions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---

# Probleme nach der Deaktivierung eines Moduls

Dieser Artikel bietet eine Lösung für Probleme mit der Modulfunktionalität, nachdem die Modulausgabe in Commerce Admin deaktiviert wurde.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.1.x oder früher
* Adobe Commerce On-Premises 2.1.X oder früher

## Problem

Wenn Sie die Modulausgabe in Commerce Admin unter **Stores** > **Settings** > **Configuration** > ADVANCED > **Advanced** deaktiviert haben, treten möglicherweise Probleme im Zusammenhang mit der Modulfunktionalität auf.

## Ursache

Durch Deaktivieren einer Modulausgabe unter **Stores** > **Settings** > **Configuration** > ADVANCED > **Advanced** wird nur die Ausgabe (HTML, JS) deaktiviert, nicht jedoch die Funktionalität dieses Moduls.

## Lösung

Wenn Sie die Modulfunktionalität deaktivieren müssen, deaktivieren Sie das Modul, wie in [Module aktivieren oder deaktivieren](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/tutorials/manage-modules) in unserer Entwicklerdokumentation beschrieben.

Die Funktion zum Deaktivieren der Modulausgabe wurde ab Version 2.2.0 entfernt.
