---
title: "Verwaltete Warnhinweise für Adobe Commerce: CPU-Warnhinweis"
description: Dieser Artikel enthält Schritte zur Fehlerbehebung, wenn Sie eine CPU-Warnmeldung für Adobe Commerce in New Relic erhalten. Um dieses Problem zu beheben, sind sofortige Maßnahmen erforderlich. Der Warnhinweis sieht je nach ausgewähltem Benachrichtigungskanal für Warnhinweise ungefähr wie folgt aus.
exl-id: 03686684-3b7e-430a-a05a-a96f38345322
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 0%

---

# Verwaltete Warnhinweise für Adobe Commerce: CPU-Warnhinweis

Dieser Artikel enthält Schritte zur Fehlerbehebung, wenn Sie eine CPU-Warnmeldung für Adobe Commerce in New Relic erhalten. Um dieses Problem zu beheben, sind sofortige Maßnahmen erforderlich. Der Warnhinweis sieht je nach ausgewähltem Benachrichtigungskanal für Warnhinweise ungefähr wie folgt aus.

![Warnung zur CPU-Warnung](assets/cpu-warning-magento-managed.png){width="500"}

## Betroffene Produkte und Versionen

Adobe Commerce on Cloud Infrastructure Pro-Planarchitektur

## Problem

Sie erhalten einen Warnhinweis in New Relic, wenn Sie sich bei [Verwaltete Warnhinweise für Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) und eine oder mehrere der Alarmschwellen überschritten wurden. Diese Warnhinweise wurden von Adobe entwickelt, um Kunden mithilfe von Einblicken aus dem Support und Engineering einen Standardsatz zu liefern.

<u> **Tu!** </u>

* Beenden Sie alle geplanten Implementierungen, bis dieser Warnhinweis gelöscht ist.
* Setzen Sie Ihre Site sofort in den Wartungsmodus, wenn Ihre Site vollständig nicht reagiert. Eine Anleitung finden Sie unter [Installationsanleitung > Wartungsmodus aktivieren oder deaktivieren](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) in unserer Entwicklerdokumentation. Stellen Sie sicher, dass Sie Ihre IP-Adresse zur Liste der ausgenommenen IP-Adressen hinzufügen, um sicherzustellen, dass Sie weiterhin auf Ihre Website zugreifen können, um die Fehlerbehebung durchzuführen. Eine Anleitung finden Sie unter [Liste der ausgenommenen IP-Adressen beibehalten](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) in unserer Entwicklerdokumentation.

<u>**Nicht!**</u>

* Starten Sie zusätzliche Marketing-Kampagnen, die zusätzliche Seitenansichten zu Ihrer Site bringen können.
* Führen Sie Indexer oder zusätzliche Crons aus, die zusätzliche Belastungen für CPU oder Festplatte verursachen können.
* Führen Sie alle wichtigen Verwaltungsaufgaben aus (z. B. Commerce-Administrator, Datenimport/-export).
* Löschen Sie den Cache.

## Lösung

Führen Sie diese Schritte aus, um die Ursache zu identifizieren und zu beheben.

1. Verwendung [Transaktionsseite des New Relic APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) zur Identifizierung von Transaktionen mit Leistungsproblemen:
   * Sortieren von Transaktionen nach aufsteigenden Apdex-Werten. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) bezieht sich auf die Benutzerzufriedenheit mit der Reaktionszeit Ihrer Webanwendungen und -dienste. [Niedriger Apdex-Wert](/help/troubleshooting/miscellaneous/troubleshoot-performance-using-new-relic-on-magento-commerce.md#low_user_satisfaction) kann einen Engpass anzeigen (eine Transaktion mit einer höheren Reaktionszeit). Normalerweise ist es die Datenbank, Redis oder PHP. Anweisungen finden Sie unter New Relic [Anzeigen von Transaktionen mit höchster Apdex-Unzufriedenheit](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Sortieren Sie Transaktionen nach höchstem Durchsatz, langsamster durchschnittlicher Antwortzeit, zeitaufwendigsten und anderen Schwellenwerten. Anweisungen finden Sie unter New Relic [Finden Sie spezifische Leistungsprobleme](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Wenn Sie immer noch Schwierigkeiten haben, die Quelle zu identifizieren, verwenden Sie [Infrastrukturseite von New Relic APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) zur Identifizierung ressourcenintensiver Dienste. Anweisungen finden Sie unter New Relic [Seite &quot;Infrastruktur-Monitoring-Hosts&quot;> Registerkarte &quot;Prozesse&quot;](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Wenn Sie die Quelle identifizieren, senden Sie SSH in die Umgebung, um weitere Untersuchungen durchzuführen. Eine Anleitung finden Sie unter [Cloud für Adobe Commerce > SSH in Ihre Umgebung](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh) in unserer Entwicklerdokumentation.
1. Wenn Sie noch immer Schwierigkeiten haben, die Quelle zu identifizieren:
   * Überprüfen Sie aktuelle Trends, um Probleme mit kürzlich durchgeführten Code-Bereitstellungen oder Konfigurationsänderungen zu identifizieren (z. B. neue Kundengruppen und große Änderungen am Katalog). Es wird empfohlen, die letzten sieben Tage der Aktivität auf Korrelationen in Code-Bereitstellungen oder Änderungen zu überprüfen.
   * Überprüfen und deaktivieren Sie flache Kataloge. Eine Anleitung finden Sie unter [Langsame Leistung, langsame und lange laufende Crons](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) in unserer Wissensdatenbank.
   * Wenn Sie vermuten, dass Sie einen DDoS-Angriff erleben, versuchen Sie, den Bot-Traffic zu blockieren. Eine Anleitung finden Sie unter [Blockieren von schädlichem Traffic für Adobe Commerce auf der schnellsten Ebene](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) in unserer Wissensdatenbank.
1. Wenn das Problem vorübergehend erscheint, führen Sie Minderungsschritte wie eine Vergrößerung durch oder platzieren Sie die Site in den Wartungsmodus. Eine Anleitung finden Sie unter [Anfordern der temporären Größenanpassung](/help/how-to/general/how-to-request-temporary-magento-upsize.md) in unserer Wissensdatenbank und [Installationsanleitung > Wartungsmodus aktivieren oder deaktivieren](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) in unserer Entwicklerdokumentation. Wenn die Upsize-Datei den normalen Betrieb der Site wiederherstellt, sollten Sie eine permanente Upsize anfordern (wenden Sie sich an Ihr Adobe Account-Team) oder versuchen, das Problem in Ihrer dedizierten Staging-Umgebung zu reproduzieren, indem Sie einen Lasttest durchführen und Abfragen optimieren oder Code verwenden, der den Druck auf Dienste verringert. Eine Anleitung finden Sie unter [Cloud für Adobe Commerce > Testbereitstellung > Belastungstests](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) in unserer Entwicklerdokumentation.
