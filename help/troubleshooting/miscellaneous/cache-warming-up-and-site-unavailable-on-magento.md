---
title: Cache-Erwärmung und Site in Adobe Commerce nicht verfügbar
description: Dieser Artikel bietet eine Lösung für den Fall, dass sich der Seiten-Cache erwärmt und eine blockierte Bereitstellung oder Site nicht vorhanden ist.
exl-id: c91d5c1f-95e6-4240-be98-2acea49ae728
feature: Cache, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Cache-Erwärmung und Site in Adobe Commerce nicht verfügbar

Dieser Artikel bietet eine Lösung für den Fall, dass sich der Seiten-Cache erwärmt und eine blockierte Bereitstellung oder Site nicht vorhanden ist.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle [unterstützte Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problem

Das Aufwärmskript für den Cache sendet am Ende der Phase nach der Bereitstellung Anforderungen mit einer derart hohen Rate, dass bestimmte Instanzen, wie z. B. 4 CPU, keine Anforderungen bewältigen können. Ihr Nginx erschöpft die Anzahl der Arbeiter.

<u>Zu reproduzierende Schritte</u>:

Starten Sie die Vorgängen zum Aufwärmen des Caches.

<u>Erwartetes Ergebnis</u>:

Seiten oder die gesamte Site werden geladen.

<u>Tatsächliches Ergebnis</u>:

Die Site ist nicht verfügbar oder die Antwortzeit ist zu hoch.

## Lösung

Schränken Sie die Anzahl der gleichzeitigen Verbindungen während der Aktualisierung des Cache ein. Dazu müssen Sie die `WARM_UP_CONCURRENCY` Variable nach der Bereitstellung , um die Anzahl der Aufwärmanforderungen anzugeben, die das Aufwärmskript für den Cache gleichzeitig senden kann. Durch das Festlegen dieser Option kann die Auslastung der Cloud-Infrastruktur von Adobe Commerce verwaltet werden. Anweisungen finden Sie unter [Variablen nach der Bereitstellung > WARM\_UP\_CONCURRENCY](https://devdocs.magento.com/cloud/env/variables-post-deploy.html#warm_up_concurrency) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

[Vollseitencache](https://docs.magento.com/user-guide/system/cache-full-page.html) in unserem Benutzerhandbuch
