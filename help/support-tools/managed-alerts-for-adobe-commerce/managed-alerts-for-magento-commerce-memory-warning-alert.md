---
title: "Verwaltete Warnhinweise für Adobe Commerce: Warnhinweis bezüglich Speicher"
description: In diesem Artikel finden Sie Schritte zur Fehlerbehebung, wenn Sie eine Speicherwarnung für Adobe Commerce in New Relic erhalten. Um dieses Problem zu beheben, sind sofortige Maßnahmen erforderlich. Der Warnhinweis sieht je nach ausgewähltem Benachrichtigungskanal für Warnhinweise ungefähr wie folgt aus.
exl-id: bb5eb3f4-b162-4737-93d5-4037f2844bb1
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 8ef51d4e6d6efa51ad4b328a48b84e10c73f3ac6
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 0%

---

# Verwaltete Warnhinweise für Adobe Commerce: Warnhinweis zur Speichernutzung

In diesem Artikel finden Sie Schritte zur Fehlerbehebung, wenn Sie eine Speicherwarnung für Adobe Commerce in New Relic erhalten. Um dieses Problem zu beheben, sind sofortige Maßnahmen erforderlich. Der Warnhinweis sieht je nach ausgewähltem Benachrichtigungskanal für Warnhinweise ungefähr wie folgt aus.

![Speicherwarnung](assets/memory-warning-magento-managed.png){width="500"}

## Betroffene Produkte und Versionen

Adobe Commerce on Cloud Infrastructure Pro-Planarchitektur

## Problem

Sie erhalten einen Warnhinweis in New Relic, wenn Sie sich bei [Verwaltete Warnhinweise für Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) und eine oder mehrere der Alarmschwellen überschritten wurden. Diese Warnhinweise wurden von Adobe Commerce entwickelt, um Kunden einen Standardsatz mit Einblicken aus dem Support und Engineering zu bieten.

<u>**Tu!**</u>:

* Es wird empfohlen, alle geplanten Implementierungen abzubrechen, bis dieser Warnhinweis gelöscht wird.
* Setzen Sie Ihre Site sofort in den Wartungsmodus, wenn Ihre Site vollständig oder gar nicht reagiert. Eine Anleitung finden Sie unter [Installationsanleitung > Wartungsmodus aktivieren oder deaktivieren](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) in unserer Entwicklerdokumentation. Stellen Sie sicher, dass Sie Ihre IP-Adresse zur Liste der ausgenommenen IP-Adressen hinzufügen, um sicherzustellen, dass Sie weiterhin auf Ihre Website zugreifen können, um die Fehlerbehebung durchzuführen. Eine Anleitung finden Sie unter [Liste der ausgenommenen IP-Adressen beibehalten](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) in unserer Entwicklerdokumentation.

<u>**Nicht!**</u>:

* Starten Sie zusätzliche Marketing-Kampagnen, die zusätzliche Seitenansichten zu Ihrer Site bringen können.
* Führen Sie Indexer oder zusätzliche Crons aus, was zusätzliche Belastungen für CPU oder Festplatte verursachen kann.
* Führen Sie alle wichtigen Verwaltungsaufgaben aus (d. h. den Administrator, Datenimport/-export).
* Löschen Sie den Cache.

## Lösung

Führen Sie diese Schritte aus, um die Ursache zu identifizieren und zu beheben.

1. Verwendung [Infrastrukturseite von New Relic APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) zur Identifizierung der wichtigsten speicherintensiven Prozesse. Anweisungen finden Sie unter New Relic [Seite &quot;Infrastruktur-Monitoring-Hosts&quot;> Registerkarte &quot;Prozesse&quot;](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes). Wenn Dienste wie Redis oder MySQL die Hauptquelle für den Speicherverbrauch sind, versuchen Sie Folgendes:

   * Vergewissern Sie sich, dass Sie die neueste Version verwenden. Neuere Versionen können manchmal Speicherlecks beheben. Wenn Sie nicht die neueste Version verwenden, sollten Sie ein Upgrade in Erwägung ziehen. Eine Anleitung finden Sie unter [Adobe Commerce auf Cloud-Infrastruktur > Dienste > Dienste ändern](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) in unserer Entwicklerdokumentation.
   * Wenn Sie immer noch nicht die Ursache für den erhöhten Speicherverbrauch ermitteln können, überprüfen Sie, ob MySQL-Probleme wie langwierige Abfragen, nicht definierte Primäre Schlüssel und doppelte Indizes vorliegen. Eine Anleitung finden Sie unter [Häufigste Datenbankprobleme in Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) in unserer Wissensdatenbank.
   * Wenn es keine MySQL-Probleme gibt, suchen Sie nach PHP-Problemen. Überprüfen laufender Prozesse durch Ausführen `ps aufx` im CLI/Terminal. In der Terminal-Ausgabe werden Cron-Aufträge und -Prozesse angezeigt, die derzeit ausgeführt werden. Überprüfen Sie die Ausgabe auf die Ausführungszeit der Prozesse. Wenn es einen Cron mit einer langen Ausführungszeit gibt, hängt der Cron möglicherweise. Siehe Abschnitt [Langsame, langsame und langwierige Crons](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) und [Cron-Auftrag blieb im Status &quot;Wird ausgeführt&quot;](/help/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.md) in unserer Support-Wissensdatenbank für Schritte zur Fehlerbehebung.

1. Wenn Sie immer noch Schwierigkeiten haben, die Ursache des Problems zu ermitteln, verwenden Sie [Transaktionsseite des New Relic APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) zur Identifizierung von Transaktionen mit Leistungsproblemen:

   * Sortieren von Transaktionen nach aufsteigenden Apdex-Werten. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) bezieht sich auf die Benutzerzufriedenheit mit der Reaktionszeit Ihrer Webanwendungen und -dienste. A [niedrige Apdex-Punktzahl](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) kann einen Engpass anzeigen (eine Transaktion mit einer höheren Reaktionszeit). Normalerweise ist es die Datenbank, Redis oder PHP. Anweisungen finden Sie unter New Relic [Anzeigen von Transaktionen mit höchster Apdex-Unzufriedenheit](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Sortieren Sie Transaktionen nach dem höchsten Durchsatz, der langsamsten durchschnittlichen Antwortzeit, dem zeitaufwendigsten und anderen Schwellenwerten. Anweisungen finden Sie unter New Relic [Finden Sie spezifische Leistungsprobleme](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Wenn Sie immer noch Schwierigkeiten haben, das Problem zu identifizieren, verwenden Sie die Infrastruktur-Seite von New Relic APM.

1. Wenn Sie die Ursache des erhöhten Speicherverbrauchs nicht identifizieren können, überprüfen Sie die aktuellen Trends, um Probleme mit kürzlich durchgeführten Code-Bereitstellungen oder Konfigurationsänderungen zu identifizieren (z. B. neue Kundengruppen und große Änderungen am Katalog). Es wird empfohlen, die letzten sieben Tage der Aktivität auf Korrelationen in Code-Bereitstellungen oder Änderungen zu überprüfen.

1. Wenn die oben genannten Methoden Ihnen nicht helfen, die Ursache und/oder Lösung innerhalb einer angemessenen Zeit zu finden, fordern Sie eine Aktualisierung an oder platzieren Sie die Site in den Wartungsmodus, falls Sie dies noch nicht getan haben. Eine Anleitung finden Sie unter [Anfordern der temporären Größenanpassung](/help/how-to/general/how-to-request-temporary-magento-upsize.md) in unserer Wissensdatenbank und [Installationsanleitung > Wartungsmodus aktivieren oder deaktivieren](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) in unserer Entwicklerdokumentation.

1. Wenn die Upsize-Datei den normalen Betrieb der Site wiederherstellt, sollten Sie eine permanente Upsize anfordern (wenden Sie sich an Ihr Adobe Account-Team) oder versuchen, das Problem in Ihrer dedizierten Staging-Umgebung zu reproduzieren, indem Sie einen Lasttest durchführen und Abfragen optimieren oder Code verwenden, der den Druck auf Dienste verringert. Siehe Abschnitt [Adobe Commerce auf Cloud-Infrastruktur > Testbereitstellung > Belastungstests](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) in unserer Entwicklerdokumentation.
