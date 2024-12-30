---
title: 'Verwaltete Warnhinweise auf Adobe Commerce: Kritischer Warnhinweis zu RediS-Speicher'
description: Dieser Artikel enthält Schritte zur Fehlerbehebung für den Fall, dass Sie einen kritischen Redis-Speicheralarm für Adobe Commerce in New Relic erhalten. Sofortiges Handeln ist erforderlich, um das Problem zu lösen. Je nach ausgewähltem Benachrichtigungskanal für Warnhinweise sieht der Warnhinweis etwa wie folgt aus.
exl-id: 28e1d879-d7ca-4439-8e81-52a1fbf3ecb0
feature: Cache, Categories, Observability, Services, Support, Tools and External Services, Variables
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 0%

---

# Verwaltete Warnhinweise auf Adobe Commerce: Kritischer Warnhinweis zu RediS-Speicher

Dieser Artikel enthält Schritte zur Fehlerbehebung für den Fall, dass Sie einen kritischen Redis-Speicheralarm für Adobe Commerce in New Relic erhalten. Sofortiges Handeln ist erforderlich, um das Problem zu lösen. Je nach ausgewähltem Benachrichtigungskanal für Warnhinweise sieht der Warnhinweis etwa wie folgt aus.

![new_relic_redis_memory_critical.png](assets/new_relic_redis_memory_critical.png)

## Betroffene Produkte und Versionen

Alle Versionen von Adobe Commerce auf Cloud-Infrastruktur Pro Planarchitektur

## Problem

Sie erhalten einen Warnhinweis in New Relic, wenn Sie sich bei [Verwaltete Warnhinweise für Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) angemeldet haben und einer oder mehrere der Warnhinweisschwellen überschritten wurden. Diese Warnhinweise wurden von Adobe entwickelt, um Händlern mithilfe von Einblicken aus Support und Engineering einen Standardsatz von Warnhinweisen bereitzustellen.

**<u>Do!</u>**

* Bricht jede geplante Bereitstellung ab, bis dieser Warnhinweis gelöscht wird.
* Setzen Sie Ihre Site sofort in den Wartungsmodus, wenn Ihre Site nicht mehr reagiert oder überhaupt nicht mehr reagiert. Anweisungen hierzu finden Sie [Installationshandbuch > Wartungsmodus aktivieren oder deaktivieren](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#enable-or-disable-maintenance-mode-1) in unserem Installationshandbuch. Fügen Sie Ihre IP-Adresse der Liste der von der Steuer befreiten IP-Adressen hinzu, um sicherzustellen, dass Sie weiterhin zur Fehlerbehebung auf Ihre Website zugreifen können. Anweisungen hierzu finden Sie unter [Liste der ausgenommenen IP-Adressen verwalten](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#maintain-the-list-of-exempt-ip-addresses) in unserem Installationshandbuch.

**<u>Tu&#39;s nicht!</u>**

* Starten Sie zusätzliche Marketing-Kampagnen, die zusätzliche Seitenansichten auf Ihre Site bringen können.
* Führen Sie Indexer oder zusätzliche Crons aus, was zu zusätzlichen Belastungen für CPU oder die Festplatte führen kann.
* Führen Sie alle wichtigen administrativen Aufgaben durch (d. h. wichtige Aktionen im Commerce-Admin, wie z. B. Datenimporte/-exporte, Leeren von Medien, Speichern von Kategorien mit einer großen Anzahl zugewiesener Produkte und Massenaktualisierungen).
* Leeren Sie den Cache.

## Lösung

Führen Sie diese Schritte aus, um die Ursache zu identifizieren und zu beheben.

**Da es sich um einen kritischen Warnhinweis handelt, wird dringend empfohlen, Schritt 1 abzuschließen, bevor Sie versuchen, das Problem zu beheben (Schritt 2 ab).**

1. Überprüfen, ob ein Adobe Commerce-Support-Ticket vorhanden ist. Anweisungen hierzu finden Sie unter [Support-Tickets nachverfolgen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) in unserer Support-Wissensdatenbank. Möglicherweise hat der Support bereits eine New Relic-Schwellenwertwarnung erhalten, ein Ticket erstellt und mit der Bearbeitung des Problems begonnen. Wenn kein Ticket vorhanden ist, erstellen Sie eines. Das Ticket sollte die folgenden Informationen enthalten:

   * Kontaktgrund: Wählen Sie „KRITISCHER New Relic-Warnhinweis empfangen“.
   * Beschreibung des Warnhinweises
   * [New Relic-Vorfall-Link](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents/). Dies ist in Ihren [Verwaltete Warnhinweise für Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) enthalten.

1. Wenn kein Support-Ticket vorhanden ist, überprüfen Sie, ob der von Redis verwendete Speicher zunimmt oder abnimmt, indem Sie zur Seite [one.newrelic.com](https://login.newrelic.com) > **Infrastruktur** > **Services von Drittanbietern** wechseln und das Redis-Dashboard auswählen. Wenn er stabil ist oder zunimmt, [ Sie ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), um den Cluster vergrößern zu lassen, oder erhöhen Sie das `maxmemory` auf die nächste Ebene.
1. Wenn Sie die Ursache für den erhöhten Redis-Speicherverbrauch nicht identifizieren können, überprüfen Sie die neuesten Trends, um Probleme mit aktuellen Code-Bereitstellungen oder Konfigurationsänderungen (z. B. neue Kundengruppen und große Änderungen am Katalog) zu identifizieren. Es wird empfohlen, die letzten sieben Tage der Aktivität auf Korrelationen in Code-Bereitstellungen oder -Änderungen zu überprüfen.
1. Überprüfen Sie, ob sich Drittanbietererweiterungen falsch verhalten:

   * Versuchen Sie, eine Korrelation mit den kürzlich installierten Erweiterungen von Drittanbietern und dem Zeitpunkt, zu dem das Problem begann, zu finden.
   * Überprüfen Sie Erweiterungen, die sich möglicherweise auf den Adobe Commerce-Cache auswirken und dazu führen können, dass der Cache schnell wächst. Dies betrifft beispielsweise benutzerdefinierte Layout-Blöcke, das Überschreiben der Cache-Funktionalität und das Speichern großer Datenmengen im Cache.

1. Wenn es keine Anzeichen für fehlerhafte Erweiterungen gibt, installieren [ die neuesten Patches, um Redis-Probleme für Adobe Commerce in der Cloud-Infrastruktur zu beheben](/help/troubleshooting/miscellaneous/install-latest-patches-to-fix-magento-redis-issues.md).
1. Wenn die oben genannten Schritte nicht dabei helfen, die Ursache des Problems zu identifizieren oder zu beheben, sollten Sie den L2-Cache aktivieren, um den Netzwerk-Traffic zwischen der App und Redis zu reduzieren. Allgemeine Informationen zum L2-Cache finden Sie unter [L2-Caching in der Adobe Commerce-](/docs/commerce-operations/configuration-guide/cache/level-two-cache.html) in unserer Entwicklerdokumentation. Um den L2-Cache für die Cloud-Infrastruktur zu aktivieren, versuchen Sie Folgendes:

   * Aktualisieren Sie die ECE-Tools, wenn diese unter Version 2002.1.2 liegen.
   * Konfigurieren Sie den L2-Cache mithilfe [Variable REDIS\_BACKEND verwenden](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) und aktualisieren Sie `.magento.env.yaml` Datei:

   ```yaml
   stage:
       deploy:
           REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
   ```
