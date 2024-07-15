---
title: Redis-Dienst abgestürzt
description: In diesem Artikel wird empfohlen, Redis zu beheben.
exl-id: 5eb8fb70-0f41-433a-8d3f-c368781a2d1d
feature: Services
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# Redis-Dienst abgestürzt

In diesem Artikel wird empfohlen, Redis zu beheben.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x
* Adobe Commerce On-Premise 2.2.x, 2.3x
* Alle Versionen von Redis

## Problem

Website-Langsamkeit oder -Ausfall aufgrund von Speicherüberlauf in Redis.

## Ursache

Speicherüberlauf kann zum Absturz des Redis-Dienstes führen. Während der Spitzenzeit benötigt der Redis-Dienst möglicherweise mehr Speicher als derzeit zugeteilt ist.

## Lösung

Um die aktuelle Konfiguration und den verwendeten Speicher zu überprüfen, führen Sie den folgenden Befehl in der CLI aus. Es wird nach verwendetem Speicher, Maxmemory, entfernten Schlüsseln und Redist up-Zeit in Tagen überprüft:

```
redis-cli -p REDIS_PORT -h REDIS_HOST info | egrep --color "(role|used_memory_peak|maxmemory|evicted_keys|uptime_in_days)"
```

Die Variablen *REDIS\_PORT* und *REDIS\_HOST* können von `app/etc/env.php` abgerufen werden.

Wenn die Ausgabe der obigen Abfrage zeigt, dass der Anteil des freien Arbeitsspeichers weniger als 40 % beträgt, senden [ein Ticket an den Adobe Commerce-Support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), um eine Erhöhung der Einstellung `maxmemory` im Redis-Server anzufordern. Wenn der Wert der entfernten Schlüssel nicht &quot;0&quot;oder der Wert für die Ladezeit in Tagen gleich 0 ist (was bedeutet, dass Redis heute abgestürzt ist), sollten Sie auch [ein Ticket an den Adobe Commerce-Support senden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), um eine Untersuchung und eine Korrektur dieses Problems anzufordern.

## Verwandte Informationen

Weitere Informationen zum Redis-Speicher finden Sie unter [Redis Memory Optimization](https://redis.io/topics/memory-optimization).
