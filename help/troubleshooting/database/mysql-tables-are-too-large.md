---
title: MySQL-Tabellen sind zu groß
description: In diesem Artikel wird erläutert, warum es ein Problem ist, wenn eine MySQL-Tabelle größer als 1 GB wird, und wie dies verhindert werden kann.
exl-id: 43f74e3b-7f2e-428c-9964-56d2ce98a34d
feature: Services
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# MySQL-Tabellen sind zu groß

In diesem Artikel wird erläutert, warum es ein Problem ist, wenn eine MySQL-Tabelle größer als 1 GB wird, und wie dies verhindert werden kann.

## Betroffene Produkte und Versionen:

* Adobe Commerce auf Cloud-Infrastruktur 2.x.x
* Adobe Commerce On-Premise 2.x.x

## Problem

Die Größe der MySQL-Tabellen wirkt sich nicht direkt auf die Site-Leistung aus. Bei einer großen Tabelle bedeutet dies jedoch, dass diese Tabelle häufig mit zusätzlichen Daten oder veralteten Daten eingefügt wird. MySQL wurde für Datenbanken entwickelt, bei denen das Verhältnis zwischen Lese-/Schreibvorgängen 80 %/20 % beträgt.  Für große Tabellen, 1 GB und mehr, könnten MySQL-Indizes, die die Leistung bei Lesevorgängen beschleunigen sollen, die Leistung bei Schreibvorgängen beeinträchtigen.

## Lösung

Beachten Sie die folgenden Optionen, um eine Leistungsminderung zu vermeiden:

* Erstellen Sie einen CRON-Auftrag, der große Tabellen bereinigt. Siehe [Große MySQL-Tabellen suchen](/help/how-to/general/find-large-mysql-tables.md) in unserer Wissensdatenbank zur Unterstützung von Empfehlungen zur Identifizierung großer Tabellen.
* Verwenden Sie für Tabellen, die größer als 1 GB sind, eine für das Schreiben von Protokollen optimierte MySQL-Engine. Beispielsweise die Archive-Engine.
* Aktualisieren Sie die Funktionalität, um zu verhindern, dass Protokolle in DB gespeichert werden.

## Verwandtes Lesen

[Übermäßige Änderungsprotokolltabellen verursachen Verzögerungen bei der Aktualisierung von Entitäten](/help/troubleshooting/database/changes-in-the-database-are-not-reflected-on-the-storefront.md) in unserer Wissensdatenbank.
