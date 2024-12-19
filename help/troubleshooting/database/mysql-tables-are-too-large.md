---
title: '[!DNL MySQL] Tabellen sind zu groß'
description: In diesem Artikel wird erläutert, warum es ein Problem darstellt, wenn eine  [!DNL MySQL] -Tabelle größer als 1 GB wird, und wie dies verhindert werden kann.
exl-id: 43f74e3b-7f2e-428c-9964-56d2ce98a34d
feature: Services
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# [!DNL MySQL] Tabellen sind zu groß

In diesem Artikel wird erläutert, warum es ein Problem darstellt, wenn eine [!DNL MySQL] Tabelle größer als 1 GB wird, und wie dies verhindert werden kann.

## Betroffene Produkte und Versionen:

* Adobe Commerce auf Cloud-Infrastruktur 2.x.x
* Adobe Commerce On-Premises 2.x.x

## Problem

Die Größe der [!DNL MySQL]-Tabellen wirkt sich nicht direkt auf die Site-Leistung aus. Wenn eine Tabelle jedoch groß ist, bedeutet dies, dass es häufige Einfügevorgänge für diese Tabelle gibt, möglicherweise mit zusätzlichen Daten oder veralteten Daten. [!DNL MySQL] wurde für Datenbanken entwickelt, bei denen das Verhältnis zwischen Lese- und Schreibvorgängen 80 %/20 % beträgt.  Bei großen Tabellen mit 1 GB und mehr können [!DNL MySQL] Indizes, die zur Beschleunigung der Leistung bei Lesevorgängen entwickelt wurden, die Leistung bei Schreibvorgängen beeinträchtigen.

## Lösung

Erwägen Sie die folgenden Optionen, um einen Leistungsabfall zu vermeiden:

* Erstellen Sie einen CRON-Auftrag, der große Tabellen bereinigt. Siehe [Finden großer  [!DNL MySQL] Tabellen](/help/how-to/general/find-large-mysql-tables.md) in unserer Support-Wissensdatenbank für Empfehlungen zum Identifizieren großer Tabellen.
* Verwenden Sie für Tabellen mit mehr als 1 GB eine für das Schreiben von Protokollen optimierte [!DNL MySQL]-Engine. Beispiel: die Archivierungs-Engine.
* Aktualisierungsfunktion, um zu vermeiden, dass Protokolle in der DB gespeichert werden.

## Verwandtes Lesen

* [Übergroße Änderungsprotokolltabellen, die zu Verzögerungen bei Entitätsaktualisierungen führen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/database/changes-in-the-database-are-not-reflected-on-the-storefront) in unserer Support-Wissensdatenbank
* [Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook
