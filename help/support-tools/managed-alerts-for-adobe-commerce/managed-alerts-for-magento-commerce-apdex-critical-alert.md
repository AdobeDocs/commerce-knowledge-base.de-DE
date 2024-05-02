---
title: "Verwaltete Warnhinweise für Adobe Commerce: kritischer Warnhinweis für Index"
description: In diesem Artikel finden Sie Schritte zur Fehlerbehebung, wenn Sie einen für Adobe Commerce kritischen Warnhinweis für New Relic erhalten. Der Apdex-Wert misst die Zufriedenheit der Benutzer mit der Reaktionszeit von Webanwendungen und -diensten. Um dieses Problem zu beheben, sind sofortige Maßnahmen erforderlich. Der Warnhinweis sieht je nach ausgewähltem Benachrichtigungskanal für Warnhinweise ungefähr wie folgt aus.
exl-id: b6d3d4f3-4abb-4285-8071-2b9fb06bfa3c
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: fbb24fb3c8b399f3b7e19c663eb4b168657498e6
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 0%

---

# Verwaltete Warnhinweise für Adobe Commerce: kritischer Warnhinweis zu Apdex

In diesem Artikel finden Sie Schritte zur Fehlerbehebung, wenn Sie einen für Adobe Commerce kritischen Warnhinweis für New Relic erhalten. Der Apdex-Wert misst die Zufriedenheit der Benutzer mit der Reaktionszeit von Webanwendungen und -diensten. Um dieses Problem zu beheben, sind sofortige Maßnahmen erforderlich. Der Warnhinweis sieht je nach ausgewähltem Benachrichtigungskanal für Warnhinweise ungefähr wie folgt aus.

![apdex-kritische Warnung](assets/apdex-critical-magento-managed.png){width="500"}

## Betroffene Produkte und Versionen

* Adobe Commerce on Cloud Infrastructure Pro-Planarchitektur
* Adobe Commerce zur Starter-Planarchitektur der Cloud-Infrastruktur

## Problem

Sie erhalten einen Warnhinweis, der in New Relic verwaltet wird, wenn Sie sich bei [Verwaltete Warnhinweise für Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) und eine oder mehrere der Alarmschwellen überschritten wurden. Diese Warnhinweise wurden von Adobe entwickelt, um Händlern mithilfe von Einblicken aus Support und Engineering einen Standardsatz zu liefern.

<u> **Tu!** </u>

* Beenden Sie alle geplanten Implementierungen, bis dieser Warnhinweis gelöscht ist.
* Setzen Sie Ihre Site sofort in den Wartungsmodus, wenn Ihre Site vollständig oder gar nicht reagiert. Eine Anleitung finden Sie unter [Installationsanleitung > Wartungsmodus aktivieren oder deaktivieren](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) in unserer Entwicklerdokumentation. Stellen Sie sicher, dass Sie Ihre IP-Adresse zur Liste der ausgenommenen IP-Adressen hinzufügen, um sicherzustellen, dass Sie weiterhin auf Ihre Website zugreifen können, um die Fehlerbehebung durchzuführen. Eine Anleitung finden Sie unter [Liste der ausgenommenen IP-Adressen beibehalten](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) in unserer Entwicklerdokumentation.

<u>**Nicht!**</u>

* Starten Sie zusätzliche Marketing-Kampagnen, die zusätzliche Seitenansichten zu Ihrer Site bringen können.
* Führen Sie Indexer oder zusätzliche Crons aus, die zusätzliche Belastungen für CPU oder Festplatte verursachen können.
* Führen Sie alle wichtigen Verwaltungsaufgaben aus (d. h. den Commerce-Administrator, Datenimporte/-exporte).
* Löschen Sie den Cache.

Wenn Sie den oben stehenden Warnhinweis erhalten haben, bevor Sie die Ursache des Warnhinweises beheben, kann dies dazu führen, dass Ihre Site nicht reagiert, wenn Sie noch keinen Site-Ausfall haben.

## Lösung

Führen Sie diese Schritte aus, um die Ursache zu identifizieren und zu beheben.

>[!WARNING]
>
>Da dies ein kritischer Warnhinweis ist, wird dringend empfohlen, **Schritt 1** bevor Sie versuchen, das Problem zu beheben (ab Schritt 2).

1. Überprüfen Sie, ob ein Adobe Commerce-Support-Ticket vorhanden ist. Eine Anleitung finden Sie unter [Support-Tickets verfolgen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) in unserer Wissensdatenbank. Der Support hat möglicherweise einen New Relic-Schwellenwert-Warnhinweis erhalten, ein Ticket erstellt und mit der Bearbeitung des Problems begonnen. Wenn kein Ticket existiert, erstellen Sie eines. Das Ticket sollte die folgenden Informationen enthalten:
   * Kontaktgrund: Wählen Sie &quot;New Relic CRITICAL alert&quot;.
   * Beschreibung der Warnung.
   * [Link zu New Relic-Vorfällen](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Dies ist in Ihrer [Verwaltete Warnhinweise für Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).
1. Um die Ursache des Problems zu ermitteln, verwenden Sie [Transaktionsseite des New Relic APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) zur Identifizierung von Transaktionen mit Leistungsproblemen:
   * Sortieren von Transaktionen nach aufsteigenden Apdex-Werten. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) bezieht sich auf die Benutzerzufriedenheit mit der Reaktionszeit Ihrer Webanwendungen und -dienste. Ein niedriger Apdex-Wert kann auf einen Engpass (eine Transaktion mit einer höheren Reaktionszeit) hinweisen. Normalerweise ist es die Datenbank, Redis oder PHP. Anweisungen finden Sie unter New Relic [Anzeigen von Transaktionen mit höchster Apdex-Unzufriedenheit](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction/#dissatisfaction).
   * Sortieren Sie Transaktionen nach dem höchsten Durchsatz, der langsamsten durchschnittlichen Antwortzeit, dem zeitaufwendigsten und anderen Schwellenwerten. Anweisungen finden Sie unter New Relic [Finden Sie spezifische Leistungsprobleme](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Wenn Sie immer noch Schwierigkeiten haben, das Problem zu identifizieren, verwenden Sie die Infrastruktur-Seite von New Relic APM.
1. Verwendung [Infrastrukturseite von New Relic APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) zur Identifizierung ressourcenintensiver Prozesse. Anweisungen finden Sie unter New Relic [Seite &quot;Infrastruktur-Monitoring-Hosts&quot;> Registerkarte &quot;Prozesse&quot;](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Wenn Dienste wie Redis oder MySQL die Hauptquelle für den Speicherverbrauch sind, versuchen Sie Folgendes:
   * Vergewissern Sie sich, dass Sie die neueste Version verwenden. Neuere Versionen können manchmal Speicherlecks beheben. Wenn Sie nicht die neueste Version verwenden, sollten Sie ein Upgrade in Erwägung ziehen. Eine Anleitung finden Sie unter [Cloud für Adobe Commerce > Dienste > Dienste ändern](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) in unserer Entwicklerdokumentation.
   * Suchen Sie nach MySQL-Problemen wie langwierigen Abfragen, nicht definierten Primären Schlüsseln und doppelten Indizes. Eine Anleitung finden Sie unter [Häufigste Datenbankprobleme in Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) in unserer Entwicklerdokumentation.
   * Überprüfen Sie auf PHP-Probleme. Überprüfen laufender Prozesse durch Ausführen `ps aufx` im CLI/Terminal. In der Terminal-Ausgabe sehen Sie Cron-Aufträge und -Prozesse, die derzeit ausgeführt werden. Überprüfen Sie die Ausgabe auf die Ausführungszeit der Prozesse. Wenn es einen Cron mit einer langen Ausführungszeit gibt, hängt der Cron möglicherweise. Informationen zur Fehlerbehebung finden Sie unter [Langsame Leistung, langsame und lange laufende Crons](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) und [Cron-Auftrag blieb im Status &quot;Wird ausgeführt&quot;](/help/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.md) in unserer Wissensdatenbank.

1. Sobald die Quelle identifiziert ist, können Sie SSH in die Umgebung eindringen, um weitere Untersuchungen durchzuführen. Eine Anleitung finden Sie unter [Cloud für Adobe Commerce > Technologien und Anforderungen > SSH in Ihre Umgebung](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh) in unserer Entwicklerdokumentation.
1. Wenn Sie nach wie vor Schwierigkeiten haben, die Quelle zu identifizieren, überprüfen Sie aktuelle Trends, um Probleme mit kürzlich durchgeführten Code-Bereitstellungen oder Konfigurationsänderungen zu identifizieren (z. B. neue Kundengruppen und große Änderungen am Katalog). Es wird empfohlen, die letzten sieben Tage der Aktivität auf Korrelationen in Code-Bereitstellungen oder Änderungen zu überprüfen.
1. Wenn Sie innerhalb einer angemessenen Zeit keine Lösung finden können, fordern Sie eine Aktualisierung an oder platzieren Sie die Site in den Wartungsmodus, falls Sie dies noch nicht getan haben. Eine Anleitung finden Sie unter [Anfordern der temporären Größenanpassung](/help/how-to/general/how-to-request-temporary-magento-upsize.md) in unserer Wissensdatenbank und [Installationsanleitung > Wartungsmodus aktivieren oder deaktivieren](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) in unserer Entwicklerdokumentation.
1. Wenn die Upsize-Datei den normalen Betrieb der Site wiederherstellt, sollten Sie eine permanente Upsize anfordern (wenden Sie sich an Ihr Adobe Account-Team) oder versuchen, das Problem in Ihrer dedizierten Staging-Umgebung zu reproduzieren, indem Sie einen Lasttest durchführen und Abfragen optimieren oder Code verwenden, der den Druck auf Dienste verringert. Siehe Abschnitt [Cloud für Adobe Commerce > Testbereitstellung > Belastungstests](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) in unserer Entwicklerdokumentation.
