---
title: '[!DNL MySQL] Tabellen sind zu groß'
description: In diesem Artikel wird erläutert, warum es ein Problem ist, wenn eine beliebige [!DNL MySQL] Tabelle größer als 1 GB wird, und wie dies verhindert werden kann.
exl-id: 43f74e3b-7f2e-428c-9964-56d2ce98a34d
feature: Services
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# [!DNL MySQL] Tabellen sind zu groß

In diesem Artikel wird erläutert, warum es ein Problem ist, wenn eine beliebige [!DNL MySQL] -Tabelle größer als 1 GB wird, und wie dies verhindert werden kann.

## Betroffene Produkte und Versionen:

* Adobe Commerce auf Cloud-Infrastruktur 2.x.x
* Adobe Commerce On-Premise 2.x.x

## Problem

Die Größe der [!DNL MySQL] Tabellen wirkt sich nicht direkt auf die Site-Leistung aus. Bei einer großen Tabelle bedeutet dies jedoch, dass diese Tabelle häufig mit zusätzlichen Daten oder veralteten Daten eingefügt wird. [!DNL MySQL] wurde für Datenbanken entwickelt, bei denen das Verhältnis zwischen Lese-/Schreibvorgängen 80 %/20 % beträgt.  Bei großen Tabellen können Indizes mit 1 GB und mehr, [!DNL MySQL], die die Leistung bei Lesevorgängen beschleunigen sollen, die Leistung bei Schreibvorgängen beeinträchtigen.

## Lösung

Beachten Sie die folgenden Optionen, um eine Leistungsminderung zu vermeiden:

* Erstellen Sie einen CRON-Auftrag, der große Tabellen bereinigt. Empfehlungen zur Identifizierung großer Tabellen finden Sie unter [Suchen großer [!DNL MySQL] Tabellen](/help/how-to/general/find-large-mysql-tables.md) in unserer Support-Wissensdatenbank.
* Verwenden Sie für Tabellen, die größer als 1 GB sind, eine für das Schreiben von Protokollen optimierte [!DNL MySQL] -Engine. Beispielsweise die Archive-Engine.
* Aktualisieren Sie die Funktionalität, um zu verhindern, dass Protokolle in DB gespeichert werden.

## Verwandtes Lesen

* [Überarbeitete Änderungsprotokolltabellen verursachen Verzögerungen bei der Aktualisierung von Entitäten](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/database/changes-in-the-database-are-not-reflected-on-the-storefront) in unserer Support-Wissensdatenbank
* [Best Practices für die Änderung von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Playbook für die Commerce-Implementierung
