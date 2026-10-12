---
title: Cache aktivieren, um Leistungseinbußen zu vermeiden
description: In diesem Artikel wird erläutert, wie Sie ein langsames Site-Problem beheben können, das durch die Deaktivierung bestimmter Adobe Commerce-Cache-Typen verursacht wird.
exl-id: e4e5a753-efa3-4552-aaf6-28e44efcfa5b
feature: Cache, Observability
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%
---
# Cache aktivieren, um Leistungseinbußen zu vermeiden

In diesem Artikel wird erläutert, wie Sie ein langsames Site-Problem beheben können, das durch die Deaktivierung bestimmter Adobe Commerce-Cache-Typen verursacht wird.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x
* Adobe Commerce On-Premises 2.2.x, 2.3.x

## Problem

Man bemerkt Leistungseinbußen. Beispielsweise wird die Checkout-Seite langsam geladen oder der Apdex-Wert sinkt in New Relic.

## Ursache

Ein Grund für Leistungseinbußen können bestimmte Adobe Commerce-Cache-Typen sein, die deaktiviert sind.

## Lösung

1. Überprüfen Sie zunächst den Status Ihres Adobe Commerce-Caches, um festzustellen, ob dies das Problem ist. Dazu [&#x200B; Sie „SSH“ in Ihre Umgebung &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh) und führen den folgenden Befehl aus:

   ```bash
   php bin/magento cache:status
   ```

   Dadurch wird der Status jedes Cache-Typs angezeigt („0“ für deaktiviert, „1“ für aktiviert). Oder Sie erhalten diese Informationen in der `app/etc/env.php`.

1. Untersuchen Sie die deaktivierten Cache-Typen. Alle Adobe Commerce-Cache-Typen sollten aktiviert werden, es sei denn, Sie haben eine alternative Anleitung von Adobe erhalten. Erweiterungen von Drittanbietern dürfen nicht die Deaktivierung des Adobe Commerce-Caches erfordern.
1. Wenn die Untersuchung bestätigt, dass einige Cache-Typen versehentlich deaktiviert sind, aktivieren Sie sie, indem Sie den folgenden Befehl für jeden Cache-Typ ausführen: `php bin/magento cache:enable <your_disabled_cache_type>`

Wenn es Bedenken und/oder Fragen dazu gibt, ob ein bestimmter Adobe Commerce-Cache-Typ deaktiviert werden kann oder sollte, [wenden Sie sich an den Adobe Commerce-Support](https://experienceleague.adobe.com/de/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide) und fragen Sie nach Empfehlungen.

## Verwandtes Lesen

Adobe Commerce-Cache-Dokumentation in unserer Entwicklerdokumentation:

* [Übersicht über den Adobe Commerce-Cache](https://developer.adobe.com/commerce/frontend-core/guide/caching)
* [Cache verwalten](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/cli/manage-cache)

Weitere mögliche Gründe für Leistungsprobleme und Lösungen für sie:

* [Adobe Commerce-Bannerausgabe deaktivieren, um die Site-Leistung zu verbessern](https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-26909)
* [MySQL-Tabellen sind zu groß](https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-26945)
* [Langsame Leistung, langsame und lange laufende Crons](https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-42802)
