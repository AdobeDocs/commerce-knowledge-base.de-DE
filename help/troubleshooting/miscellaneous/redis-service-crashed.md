---
title: Redis-Dienst abgestürzt
description: Der Artikel empfiehlt, Redis zu beheben.
exl-id: 5eb8fb70-0f41-433a-8d3f-c368781a2d1d
feature: Services
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# Redis-Dienst abgestürzt

Der Artikel empfiehlt, Redis zu beheben.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x
* Adobe Commerce On-Premises 2.2.x., 2.3x
* Alle Versionen von Redis

## Problem

Langsamkeit oder Ausfall der Website aufgrund eines Speicherüberlaufs in Redis.

## Ursache

Ein Speicherüberlauf kann dazu führen, dass der Redis-Dienst abstürzt. Während der Spitzenzeiten benötigt der Redis-Service möglicherweise mehr Speicher als derzeit zugewiesen ist.

## Lösung

Um die aktuelle Konfiguration und den verwendeten Speicher zu überprüfen, führen Sie den folgenden Befehl in der CLI aus. Er sucht nach belegtem Speicher, maximalem Speicher, entfernten Schlüsseln und Redi-up-Zeit in Tagen:

```
redis-cli -p REDIS_PORT -h REDIS_HOST info | egrep --color "(role|used_memory_peak|maxmemory|evicted_keys|uptime_in_days)"
```

Die *REDIS\_PORT* und *REDIS\_HOST*-Variablen können von `app/etc/env.php` abgerufen werden.

Wenn die Ausgabe der obigen Abfrage zeigt, dass der Prozentsatz des freien Speichers weniger als 40 % beträgt, [senden Sie ein Ticket an den Adobe Commerce-Support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) und fordern Sie eine Erhöhung der `maxmemory` im Redis-Server an. Wenn der Wert der entfernten Schlüssel nicht „0“ ist oder die Redis-Betriebszeit in Tagen gleich 0 (was anzeigt, dass Redis heute abgestürzt ist), sollten Sie auch [ein Ticket an den Adobe Commerce-Support senden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) um eine Untersuchung und eine Korrektur dieses Problems bitten.

## Verwandtes Lesen

Weitere Informationen zum Redis-Speicher finden Sie unter [Redis-Speicheroptimierung](https://redis.io/topics/memory-optimization).
