---
title: "Verwaltete Warnhinweise zu Adobe Commerce: speicherkritischer Warnhinweis"
description: Dieser Artikel enthält Schritte zur Fehlerbehebung, wenn Sie eine speicherkritische Warnung für Adobe Commerce in New Relic erhalten. Um dieses Problem zu beheben, sind sofortige Maßnahmen erforderlich. Der Warnhinweis sieht je nach ausgewähltem Benachrichtigungskanal für Warnhinweise ungefähr wie folgt aus.
exl-id: feed7998-c50b-4cbf-a92d-cbfc65745a1c
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 468ad1c47da3c299b8028726e79e25a4aa9489ea
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 0%

---

# Verwaltete Warnhinweise zu Adobe Commerce: speicherkritische Warnhinweise

Dieser Artikel enthält Schritte zur Fehlerbehebung, wenn Sie eine speicherkritische Warnung für Adobe Commerce in New Relic erhalten. Um dieses Problem zu beheben, sind sofortige Maßnahmen erforderlich. Der Warnhinweis sieht je nach ausgewähltem Benachrichtigungskanal für Warnhinweise ungefähr wie folgt aus.

![Festplattenkritischer Warnhinweis](assets/memory-critical-magento-managed.png){width="500"}

## Betroffene Produkte und Versionen

Alle Versionen von Adobe Commerce auf der Cloud Infrastructure Pro Plan-Architektur.

## Problem

Sie erhalten einen Warnhinweis, der in New Relic verwaltet wird, wenn Sie sich bei [Verwaltete Warnhinweise für Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) und eine oder mehrere der Alarmschwellen überschritten wurden. Diese Warnhinweise wurden von Adobe entwickelt, um Kunden mithilfe von Einblicken aus dem Support und Engineering einen Standardsatz zu liefern.

<u> **Tu!** </u>

* Geplante Bereitstellung abbrechen, bis dieser Warnhinweis gelöscht ist
* Setzen Sie Ihre Site sofort in den Wartungsmodus, wenn Ihre Site vollständig oder gar nicht reagiert. Anweisungen finden Sie unter [Installationsanleitung > Wartungsmodus aktivieren oder deaktivieren](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) in unserer Entwicklerdokumentation. Stellen Sie sicher, dass Sie Ihre IP-Adresse zur Liste der ausgenommenen IP-Adressen hinzufügen, um sicherzustellen, dass Sie weiterhin auf Ihre Website zugreifen können, um die Fehlerbehebung durchzuführen. Anweisungen finden Sie unter [Liste der ausgenommenen IP-Adressen beibehalten](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) in unserer Entwicklerdokumentation.

<u>**Nicht!**</u>

* Starten Sie zusätzliche Marketing-Kampagnen, die zusätzliche Seitenansichten zu Ihrer Site bringen können.
* Führen Sie Indexer oder zusätzliche Crons aus, die zusätzliche Belastungen für CPU oder Festplatte verursachen können.
* Führen Sie alle wichtigen Verwaltungsaufgaben aus (z. B. Commerce-Administrator, Datenimport/-export).
* Löschen Sie den Cache.

Ihre Site reagiert möglicherweise nicht mehr (wenn Sie noch keinen Site-Ausfall haben), wenn Sie eine der &quot;Don&#39;t&quot;-Aktionen ausführen, bevor Sie die Ursache des Warnhinweises untersucht und gelöst haben.

## Lösung

Führen Sie diese Schritte aus, um die Ursache zu identifizieren und zu beheben.

>[!WARNING]
>
>Da dies ein kritischer Warnhinweis ist, wird dringend empfohlen, **Schritt 1** bevor Sie versuchen, das Problem zu beheben (ab Schritt 2).

1. Überprüfen Sie, ob ein Adobe Commerce-Support-Ticket vorhanden ist. Anweisungen finden Sie unter [Support-Tickets verfolgen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) in unserer Wissensdatenbank. Möglicherweise hat der Support bereits eine New Relic-Schwellenwarnung erhalten, ein Ticket erstellt und mit der Bearbeitung des Problems begonnen. Wenn kein Ticket existiert, erstellen Sie eines. Das Ticket sollte die folgenden Informationen enthalten:
   * Kontaktgrund: Wählen Sie &quot;New Relic CRITICAL alert&quot;.
   * Beschreibung der Warnung
   * [Link zu New Relic-Vorfällen](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Dies ist in Ihrer [Verwaltete Warnhinweise für Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).

1. Verwendung [Infrastrukturseite von New Relic APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) zur Identifizierung der wichtigsten speicherintensiven Prozesse. Anweisungen finden Sie unter New Relic [Seite &quot;Infrastruktur-Monitoring-Hosts&quot;> Registerkarte &quot;Prozesse&quot;](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes):
   * Wenn Dienste wie Redis, MySQL oder PHP die wichtigsten Quellen für den Speicherverbrauch sind, versuchen Sie Folgendes:
1. Vergewissern Sie sich, dass Sie die neuesten Versionen verwenden. Neuere Versionen können manchmal Speicherlecks beheben. Wenn Sie nicht die neueste Version verwenden, sollten Sie ein Upgrade in Erwägung ziehen. Eine Anleitung finden Sie unter [Adobe Commerce auf Cloud-Infrastruktur > Dienste > Dienste ändern](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) in unserer Entwicklerdokumentation.
1. Wenn das Problem mit dem Dienst nicht versionsbezogen ist, versuchen Sie Folgendes:
1. **MySQL**: Suchen Sie nach Problemen wie langwierigen Abfragen, nicht definierten Primären Schlüsseln und doppelten Indizes. Eine Anleitung finden Sie unter [Häufigste Datenbankprobleme in Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) in unserer Wissensdatenbank.
1. **Redis**: Wenn Redis eine der wichtigsten Quellen für den Speicherverbrauch ist, [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
1. **PHP**: Wenn PHP eine der wichtigsten Quellen für Speicherverbrauch ist, überprüfen Sie laufende Prozesse, indem Sie `ps aufx` im CLI/Terminal. In der Terminal-Ausgabe sehen Sie Cron-Aufträge und -Prozesse, die derzeit ausgeführt werden. Überprüfen Sie die Ausgabe auf die Ausführungszeit der Prozesse. Wenn es einen Cron mit einer langen Ausführungszeit gibt, hängt der Cron möglicherweise. Informationen zur Fehlerbehebung finden Sie unter [Langsame Leistung, langsame und lange laufende Crons](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) und [Cron-Auftrag blieb im Status &quot;Wird ausgeführt&quot;](https://support.magento.com/hc/en-us/articles/360033099451) in unserer Wissensdatenbank.
1. Wenn Sie immer noch Schwierigkeiten haben, die Ursache des Problems zu ermitteln, verwenden Sie [Transaktionsseite des New Relic APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) zur Identifizierung von Transaktionen mit Leistungsproblemen:
   * Sortieren von Transaktionen nach aufsteigenden Apdex-Werten. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) bezieht sich auf die Benutzerzufriedenheit mit der Reaktionszeit Ihrer Webanwendungen und -dienste. A [niedrige Apdex-Punktzahl](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) kann einen Engpass anzeigen (eine Transaktion mit einer höheren Reaktionszeit). Normalerweise ist es die Datenbank, Redis oder PHP. Anweisungen finden Sie unter New Relic [Anzeigen von Transaktionen mit höchster Apdex-Unzufriedenheit](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Sortieren Sie Transaktionen nach dem höchsten Durchsatz, der langsamsten durchschnittlichen Antwortzeit, dem zeitaufwendigsten und anderen Schwellenwerten. Anweisungen finden Sie unter New Relic [Finden Sie spezifische Leistungsprobleme](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Wenn Sie immer noch Schwierigkeiten haben, das Problem zu identifizieren, verwenden Sie die Infrastruktur-Seite von New Relic APM.
1. Wenn Sie die Ursache des erhöhten Speicherverbrauchs nicht identifizieren können, überprüfen Sie die aktuellen Trends, um Probleme mit kürzlich durchgeführten Code-Bereitstellungen oder Konfigurationsänderungen zu identifizieren (z. B. neue Kundengruppen und große Änderungen am Katalog). Es wird empfohlen, die letzten sieben Tage der Aktivität auf Korrelationen in Codebereitstellungen oder Änderungen zu überprüfen.
1. Wenn die oben genannten Methoden Ihnen nicht helfen, die Ursache und/oder Lösung innerhalb einer angemessenen Zeit zu finden, fordern Sie eine Aktualisierung an oder platzieren Sie die Site in den Wartungsmodus, falls Sie dies noch nicht getan haben. Anweisungen finden Sie unter [Anfordern der temporären Größenanpassung](/help/how-to/general/how-to-request-temporary-magento-upsize.md) in unserer Wissensdatenbank und [Installationsanleitung > Wartungsmodus aktivieren oder deaktivieren](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) in unserer Entwicklerdokumentation.
1. Wenn die Upsize-Datei den normalen Betrieb der Site wiederherstellt, sollten Sie eine permanente Upsize anfordern (wenden Sie sich an Ihr Adobe Account-Team) oder versuchen, das Problem in Ihrer dedizierten Staging-Umgebung zu reproduzieren, indem Sie einen Lasttest durchführen und Abfragen optimieren oder Code verwenden, der den Druck auf Dienste verringert. Siehe [Adobe Commerce auf Cloud-Infrastruktur > Testbereitstellung > Belastungstests](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) in unserer Entwicklerdokumentation.
