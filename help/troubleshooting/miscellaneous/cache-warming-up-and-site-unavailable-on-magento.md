---
title: Cache-Aufwärmung und Site auf Adobe Commerce nicht verfügbar
description: Dieser Artikel bietet eine Lösung für den Fall, dass sich der Seiten-Cache erwärmt und eine Bereitstellung oder Site hängen geblieben ist.
exl-id: c91d5c1f-95e6-4240-be98-2acea49ae728
feature: Cache, Variables
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Cache-Aufwärmung und Site auf Adobe Commerce nicht verfügbar

Dieser Artikel bietet eine Lösung für den Fall, dass sich der Seiten-Cache erwärmt und eine Bereitstellung oder Site hängen geblieben ist.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, alle [unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problem

Das Skript zum Aufwärmen des Caches sendet am Ende der Phase nach der Bereitstellung Anfragen mit einer so hohen Rate, dass bestimmte Instanzen, z. B. 4-CPU-Instanzen, sie nicht bewältigen können. Ihr Einkommen erschöpft die Anzahl der Arbeiter.

<u>Schritte zur Reproduktion</u>:

Cache-Aufwärmvorgänge starten.

<u>Erwartetes Ergebnis</u>:

Seiten oder Ladevorgänge der gesamten Site.

<u>Tatsächliches </u>:

Die Site ist nicht verfügbar oder die Antwortzeit ist zu hoch.

## Lösung

Begrenzen Sie die Anzahl der gleichzeitigen Verbindungen während des Aufwärmens des Cache. Dazu muss die Variable `WARM_UP_CONCURRENCY` nach der Bereitstellung hinzugefügt werden, um die Anzahl der Aufwärmanforderungen anzugeben, die das Cache-Aufwärmskript gleichzeitig senden kann. Das Festlegen dieser Option kann die Auslastung der Cloud-Infrastruktur von Adobe Commerce verringern. Anweisungen hierzu finden Sie [Variablen nach der Bereitstellung > WARM\_UP\_CONCURRENCY](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-post-deploy#warm_up_concurrency) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

[Vollständiger Seitencache](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#full-page-caching) in unserem Benutzerhandbuch
