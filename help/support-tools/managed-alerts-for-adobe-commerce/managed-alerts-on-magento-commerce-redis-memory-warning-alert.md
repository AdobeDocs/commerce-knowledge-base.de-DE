---
title: 'Verwaltete Warnhinweise auf Adobe Commerce: Warnung bei Redis-Speicher'
description: 'Dieser Artikel enthält Schritte zur Fehlerbehebung für den Fall, dass Sie einen Redis-Warnhinweis für Adobe Commerce in New Relic erhalten. Sofortiges Handeln ist erforderlich, um das Problem zu lösen. Der Warnhinweis sieht je nach ausgewähltem Benachrichtigungskanal wie folgt aus:'
exl-id: b7867a42-3817-4cb4-93cf-d69acee33a41
feature: Categories, Marketing Tools, Observability, Services, Support, Tools and External Services, Variables
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# Verwaltete Warnhinweise auf Adobe Commerce: Warnung bei Redis-Speicher

Dieser Artikel enthält Schritte zur Fehlerbehebung für den Fall, dass Sie einen Redis-Warnhinweis für Adobe Commerce in New Relic erhalten. Sofortiges Handeln ist erforderlich, um das Problem zu lösen. Der Warnhinweis sieht je nach ausgewähltem Benachrichtigungskanal wie folgt aus:

![new_relic_redis_memory_warning.png](assets/new_relic_redis_memory_warning.png)

## Betroffene Produkte und Versionen

Alle Versionen von Adobe Commerce auf Cloud-Infrastruktur Pro planen Architektur.

## Problem

Sie erhalten einen Warnhinweis in New Relic, wenn Sie sich bei [Verwaltete Warnhinweise für Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) angemeldet haben und einer oder mehrere der Warnhinweisschwellen überschritten wurden. Diese Warnhinweise wurden von Adobe entwickelt, um Händlern mithilfe von Einblicken aus Support und Engineering einen Standardsatz von Warnhinweisen bereitzustellen.

**<u>Do!</u>**

* Es wird empfohlen, alle geplanten Bereitstellungen abzubrechen, bis dieser Warnhinweis gelöscht wird.
* Wenn Ihre Site nicht mehr reagiert oder nicht mehr reagiert, setzen Sie Ihre Site sofort in den Wartungsmodus. Anweisungen hierzu finden Sie [Installationshandbuch > Wartungsmodus aktivieren oder deaktivieren](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#enable-or-disable-maintenance-mode-1) in unserem Installationshandbuch.
* Fügen Sie Ihre IP-Adresse der Liste der von der Steuer befreiten IP-Adressen hinzu, um sicherzustellen, dass Sie weiterhin zur Fehlerbehebung auf Ihre Website zugreifen können. Anweisungen hierzu finden Sie unter [Liste der ausgenommenen IP-Adressen verwalten](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#maintain-the-list-of-exempt-ip-addresses) in unserem Installationshandbuch.

**<u>Tu&#39;s nicht!</u>**

* Starten Sie zusätzliche Marketing-Kampagnen, die zusätzliche Seitenansichten auf Ihre Site bringen können.
* Führen Sie Indexer oder zusätzliche Crons aus, was zu zusätzlichen Belastungen für CPU oder die Festplatte führen kann.
* Führen Sie alle wichtigen administrativen Aufgaben durch (d. h. wichtige Aktionen im Commerce-Admin, z. B. Datenimporte/-exporte, Leeren von Medien, Speichern von Kategorien mit einer großen Anzahl zugewiesener Produkte und Massenaktualisierungen).
* Leeren Sie den Cache.

## Lösung

Führen Sie diese Schritte aus, um die Ursache zu identifizieren und zu beheben.

1. Überprüfen Sie, ob der von Redis verwendete Speicher zunimmt oder abnimmt, indem Sie zur Seite [one.newrelic.com](https://login.newrelic.com/login) > **Infrastructure** > **Services von Drittanbietern** wechseln und das Redis-Dashboard auswählen. Wenn er stabil ist oder zunimmt, [ Sie ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), um den Cluster vergrößern zu lassen, oder erhöhen Sie das `maxmemory` auf die nächste Ebene.
1. Wenn Sie die Ursache für den erhöhten Redis-Speicherverbrauch nicht identifizieren können, überprüfen Sie die neuesten Trends, um Probleme mit aktuellen Code-Bereitstellungen oder Konfigurationsänderungen (z. B. neue Kundengruppen und große Änderungen am Katalog) zu identifizieren. Es wird empfohlen, die letzten sieben Tage der Aktivität auf Korrelationen in Code-Bereitstellungen oder -Änderungen zu überprüfen.
1. Überprüfen Sie, ob sich Drittanbietererweiterungen falsch verhalten:
   * Versuchen Sie, eine Korrelation mit den kürzlich installierten Erweiterungen von Drittanbietern und dem Zeitpunkt, zu dem das Problem begann, zu finden.
   * Überprüfen Sie Erweiterungen, die sich möglicherweise auf den Adobe Commerce-Cache auswirken und dazu führen können, dass der Cache schnell wächst. Dies betrifft beispielsweise benutzerdefinierte Layout-Blöcke, das Überschreiben der Cache-Funktionalität und das Speichern großer Datenmengen im Cache.
1. Wenn es keine Anzeichen für fehlerhafte Erweiterungen gibt, installieren [ die neuesten Patches, um Redis-Probleme für Adobe Commerce in der Cloud-Infrastruktur zu beheben](/help/troubleshooting/miscellaneous/install-latest-patches-to-fix-magento-redis-issues.md). Wenn die oben genannten Schritte nicht dabei helfen, die Ursache des Problems zu identifizieren oder zu beheben, sollten Sie den L2-Cache aktivieren, um den Netzwerk-Traffic zwischen der App und Redis zu reduzieren. Allgemeine Informationen zum L2-Cache finden Sie unter [L2-Caching in der Adobe Commerce-Anwendung](/docs/commerce-operations/configuration-guide/cache/level-two-cache.html) in unserem Konfigurationshandbuch. Um den L2-Cache für die Cloud-Infrastruktur zu aktivieren, versuchen Sie Folgendes:
   * Aktualisieren Sie die ECE-Tools, wenn diese unter Version 2002.1.2 liegen.
   * Konfigurieren Sie den L2-Cache mithilfe [Variable REDIS\_BACKEND verwenden](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) und aktualisieren Sie `.magento.env.yaml` Datei:

   ```yaml
   stage:
      deploy:
          REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
   ```
