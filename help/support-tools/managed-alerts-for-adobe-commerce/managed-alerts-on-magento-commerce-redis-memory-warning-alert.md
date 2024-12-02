---
title: 'Verwaltete Warnhinweise für Adobe Commerce: Warnhinweis zur Speicherüberarbeitung'
description: 'In diesem Artikel finden Sie Schritte zur Fehlerbehebung, die durchgeführt werden müssen, wenn Sie einen Warnhinweis für Adobe Commerce in New Relic erhalten. Zur Lösung des Problems ist eine sofortige Aktion erforderlich. Der Warnhinweis sieht je nach ausgewähltem Benachrichtigungskanal wie folgt aus:'
exl-id: b7867a42-3817-4cb4-93cf-d69acee33a41
feature: Categories, Marketing Tools, Observability, Services, Support, Tools and External Services, Variables
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# Verwaltete Warnhinweise für Adobe Commerce: Warnhinweis zur Speicherüberarbeitung

In diesem Artikel finden Sie Schritte zur Fehlerbehebung, die durchgeführt werden müssen, wenn Sie einen Warnhinweis für Adobe Commerce in New Relic erhalten. Zur Lösung des Problems ist eine sofortige Aktion erforderlich. Der Warnhinweis sieht je nach ausgewähltem Benachrichtigungskanal wie folgt aus:

![new_relic_redis_memory_warning.png](assets/new_relic_redis_memory_warning.png)

## Betroffene Produkte und Versionen

Alle Versionen von Adobe Commerce auf der Cloud Infrastructure Pro Plan-Architektur.

## Problem

Sie erhalten eine Warnung in New Relic, wenn Sie bis zu [Warnhinweise für Adobe Commerce verwalten](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) angemeldet haben und mindestens eine der Warnschwellen überschritten wurde. Diese Warnhinweise wurden von Adobe entwickelt, um Händlern mithilfe von Einblicken aus Support und Engineering einen Standardsatz von Warnhinweisen zu geben.

**<u>Do!</u>**

* Es wird empfohlen, alle geplanten Implementierungen abzubrechen, bis dieser Warnhinweis gelöscht wird.
* Wenn Ihre Site vollständig reagiert oder nicht mehr reagiert, stellen Sie Ihre Site sofort in den Wartungsmodus. Anweisungen finden Sie unter [Installationshandbuch > Wartungsmodus aktivieren oder deaktivieren](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#enable-or-disable-maintenance-mode-1) in unserem Installationshandbuch.
* Stellen Sie sicher, dass Sie Ihre IP-Adresse zur Liste der ausgenommenen IP-Adressen hinzufügen, um sicherzustellen, dass Sie weiterhin auf Ihre Website zugreifen können, um die Fehlerbehebung durchzuführen. Anweisungen finden Sie unter [Verwalten der Liste der ausgenommenen IP-Adressen](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#maintain-the-list-of-exempt-ip-addresses) in unserem Installationshandbuch.

**<u>Nicht!</u>**

* Starten Sie zusätzliche Marketing-Kampagnen, die zusätzliche Seitenansichten zu Ihrer Site bringen können.
* Führen Sie Indexer oder zusätzliche Crons aus, die zusätzliche Belastungen für CPU oder Festplatte verursachen können.
* Führen Sie alle wichtigen Verwaltungsaufgaben aus (d. h. größere Aktionen im Commerce-Administrator, z. B. Datenimport/-export, Flushing von Medien, Speichern von Kategorien mit einer großen Anzahl zugewiesener Produkte und Massenaktualisierungen).
* Löschen Sie den Cache.

## Lösung

Führen Sie diese Schritte aus, um die Ursache zu identifizieren und zu beheben.

1. Überprüfen Sie, ob der verwendete Redis-Speicher zunimmt oder abnimmt, indem Sie zur Seite [one.newrelic.com](https://login.newrelic.com/login) > **Infrastructure** > **Drittanbieterdienste** navigieren, und wählen Sie das Redis-Dashboard aus. Wenn es stabil ist oder zunimmt, senden [ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), um den Cluster zu aktualisieren, oder erhöhen Sie die `maxmemory` -Grenze auf die nächste Ebene.
1. Wenn Sie die Ursache des erhöhten Redis-Speicherverbrauchs nicht identifizieren können, überprüfen Sie die aktuellen Trends, um Probleme mit kürzlich durchgeführten Code-Bereitstellungen oder Konfigurationsänderungen zu identifizieren (z. B. neue Kundengruppen und große Änderungen am Katalog). Es wird empfohlen, die letzten sieben Tage der Aktivität auf Korrelationen in Code-Bereitstellungen oder Änderungen zu überprüfen.
1. Überprüfen Sie, ob Drittanbietererweiterungen fehlschlagen:
   * Suchen Sie nach einer Korrelation mit kürzlich installierten Drittanbietererweiterungen und dem Zeitpunkt, zu dem das Problem gestartet wurde.
   * Überprüfen Sie Erweiterungen, die sich möglicherweise auf den Adobe Commerce-Cache auswirken und dazu führen können, dass der Cache schnell wächst. Beispielsweise benutzerdefinierte Layout-Bausteine, das Überschreiben der Cache-Funktionalität und das Speichern großer Datenmengen im Cache.
1. Wenn keine Hinweise auf ein falsches Verhalten von Erweiterungen vorliegen, installieren Sie die neuesten Patches, um Redis-Probleme für Adobe Commerce in der Cloud-Infrastruktur zu beheben.](/help/troubleshooting/miscellaneous/install-latest-patches-to-fix-magento-redis-issues.md) [ Wenn die oben genannten Schritte Ihnen nicht dabei helfen, die Ursache des Problems zu identifizieren oder zu beheben, sollten Sie erwägen, den L2-Cache zu aktivieren, um den Netzwerkverkehr zwischen der App und Redis zu reduzieren. Allgemeine Informationen zum L2-Cache finden Sie unter [L2-Zwischenspeicherung in der Adobe Commerce-Anwendung](/docs/commerce-operations/configuration-guide/cache/level-two-cache.html) in unserem Konfigurationshandbuch. Um den L2-Cache für die Cloud-Infrastruktur zu aktivieren, versuchen Sie Folgendes:
   * Aktualisieren Sie die ECE-Tools, wenn die Version 2002.1.2 nicht erreicht wurde.
   * Konfigurieren Sie den L2-Cache mithilfe von [Verwenden der REDIS\_BACKEND-Variablen](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) und Aktualisieren der `.magento.env.yaml` -Datei:

   ```yaml
   stage:
      deploy:
          REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
   ```
