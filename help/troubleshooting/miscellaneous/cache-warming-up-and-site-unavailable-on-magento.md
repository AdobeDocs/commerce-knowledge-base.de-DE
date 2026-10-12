---
title: Cache-Aufwärmung und Site auf Adobe Commerce nicht verfügbar
description: Dieser Artikel bietet eine Lösung für den Fall, dass sich der Seiten-Cache erwärmt und eine Bereitstellung oder Site hängen geblieben ist.
exl-id: c91d5c1f-95e6-4240-be98-2acea49ae728
feature: Cache, Variables
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: 2191e157-828a-5358-ad69-ebcaa8402915
    internal-label: Variables
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '248'
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
