---
title: Cache aktivieren, um Leistungseinbußen zu vermeiden
description: In diesem Artikel wird erläutert, wie Sie ein langsames Site-Problem beheben können, das durch die Deaktivierung bestimmter Adobe Commerce-Cache-Typen verursacht wird.
exl-id: e4e5a753-efa3-4552-aaf6-28e44efcfa5b
feature: Cache, Observability
role: Developer
source-git-commit: bd6aa238ff8273c60a4cf5160fb614de6ff00d21
workflow-type: tm+mt
source-wordcount: '292'
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

1. Überprüfen Sie zunächst den Status Ihres Adobe Commerce-Caches, um festzustellen, ob dies das Problem ist. Dazu [ Sie „SSH“ in Ihre Umgebung ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh) und führen den folgenden Befehl aus:

   ```bash
   php bin/magento cache:status
   ```

   Dadurch wird der Status jedes Cache-Typs angezeigt („0“ für deaktiviert, „1“ für aktiviert). Oder Sie erhalten diese Informationen in der `app/etc/env.php`.

1. Untersuchen Sie die deaktivierten Cache-Typen. Alle Adobe Commerce-Cache-Typen sollten aktiviert werden, es sei denn, Sie haben eine alternative Anleitung von Adobe erhalten. Erweiterungen von Drittanbietern dürfen nicht die Deaktivierung des Adobe Commerce-Caches erfordern.
1. Wenn die Untersuchung bestätigt, dass einige Cache-Typen versehentlich deaktiviert sind, aktivieren Sie sie, indem Sie den folgenden Befehl für jeden Cache-Typ ausführen: `php bin/magento cache:enable <your_disabled_cache_type>`

Wenn es Bedenken und/oder Fragen dazu gibt, ob ein bestimmter Adobe Commerce-Cache-Typ deaktiviert werden kann oder sollte, [wenden Sie sich an den Adobe Commerce-Support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) und fragen Sie nach Empfehlungen.

## Verwandtes Lesen

Adobe Commerce-Cache-Dokumentation in unserer Entwicklerdokumentation:

* [Übersicht über den Adobe Commerce-Cache](https://developer.adobe.com/commerce/frontend-core/guide/caching/)
* [Cache verwalten](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-cache)

Weitere mögliche Gründe für Leistungsprobleme und Lösungen für sie:

* [Deaktivieren der Adobe Commerce-Bannerausgabe zur Verbesserung der Site-Leistung](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26909)
* [MySQL-Tabellen sind zu groß](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26945)
* [Langsame Leistung, langsame und lange laufende Crons](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md)
* [Eingeschränkter Admin-Zugriff, der Leistungsprobleme verursacht](/help/troubleshooting/miscellaneous/restricted-admin-access-causing-performance-issues.md)
