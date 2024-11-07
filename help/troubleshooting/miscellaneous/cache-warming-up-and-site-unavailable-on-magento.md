---
title: Cache-Erwärmung und Site in Adobe Commerce nicht verfügbar
description: Dieser Artikel bietet eine Lösung für den Fall, dass sich der Seiten-Cache erwärmt und eine blockierte Bereitstellung oder Site nicht vorhanden ist.
exl-id: c91d5c1f-95e6-4240-be98-2acea49ae728
feature: Cache, Variables
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Cache-Erwärmung und Site in Adobe Commerce nicht verfügbar

Dieser Artikel bietet eine Lösung für den Fall, dass sich der Seiten-Cache erwärmt und eine blockierte Bereitstellung oder Site nicht vorhanden ist.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle [unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problem

Das Aufwärmskript für den Cache sendet am Ende der Phase nach der Bereitstellung Anforderungen mit einer derart hohen Rate, dass bestimmte Instanzen, wie z. B. 4 CPU, keine Anforderungen bewältigen können. Ihr Nginx erschöpft die Anzahl der Arbeiter.

<u>Zu reproduzierende Schritte</u>:

Starten Sie die Vorgängen zum Aufwärmen des Caches.

<u>Erwartetes Ergebnis</u>:

Seiten oder die gesamte Site werden geladen.

<u>Tatsächliches Ergebnis</u>:

Die Site ist nicht verfügbar oder die Antwortzeit ist zu hoch.

## Lösung

Schränken Sie die Anzahl der gleichzeitigen Verbindungen während der Aktualisierung des Cache ein. Dazu muss die Variable &quot;`WARM_UP_CONCURRENCY` nach der Bereitstellung&quot;hinzugefügt werden, um die Anzahl der Aufwärmanforderungen anzugeben, die das Aufwärmskript für den Cache gleichzeitig senden kann. Durch das Festlegen dieser Option kann die Auslastung der Cloud-Infrastruktur von Adobe Commerce verwaltet werden. Anweisungen finden Sie unter [Variablen nach der Bereitstellung > WARM\_UP\_CONCURRENCY](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-post-deploy#warm_up_concurrency) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

[Vollseitencache](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#full-page-caching) in unserem Benutzerhandbuch
