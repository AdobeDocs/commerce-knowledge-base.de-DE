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

![CPU-Warnhinweis](assets/cpu-warning-magento-managed.png){width="500"}

## Betroffene Produkte und Versionen

Adobe Commerce on Cloud Infrastructure Pro-Planarchitektur

## Problem

Sie erhalten eine Warnung in New Relic, wenn Sie bis zu [Warnhinweise für Adobe Commerce verwalten](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) angemeldet haben und mindestens eine der Warnschwellen überschritten wurde. Diese Warnhinweise wurden von Adobe entwickelt, um Kunden mithilfe von Einblicken aus dem Support und Engineering einen Standardsatz zu liefern.

<u> **Do!** </u>

* Beenden Sie alle geplanten Implementierungen, bis dieser Warnhinweis gelöscht ist.
* Setzen Sie Ihre Site sofort in den Wartungsmodus, wenn Ihre Site vollständig nicht reagiert. Anweisungen finden Sie unter [Installationshandbuch > Wartungsmodus aktivieren oder deaktivieren](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) in unserer Entwicklerdokumentation. Stellen Sie sicher, dass Sie Ihre IP-Adresse zur Liste der ausgenommenen IP-Adressen hinzufügen, um sicherzustellen, dass Sie weiterhin auf Ihre Website zugreifen können, um die Fehlerbehebung durchzuführen. Anweisungen finden Sie unter [Verwalten der Liste der ausgenommenen IP-Adressen](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) in unserer Entwicklerdokumentation.

<u>**Nicht!**</u>

* Starten Sie zusätzliche Marketing-Kampagnen, die zusätzliche Seitenansichten zu Ihrer Site bringen können.
* Führen Sie Indexer oder zusätzliche Crons aus, die zusätzliche Belastungen für CPU oder Festplatte verursachen können.
* Führen Sie alle wichtigen Verwaltungsaufgaben aus (z. B. Commerce-Administrator, Datenimport/-export).
* Löschen Sie den Cache.

## Lösung

Führen Sie diese Schritte aus, um die Ursache zu identifizieren und zu beheben.

1. Verwenden Sie die [Transaktionsseite des New Relic-APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems), um Transaktionen mit Leistungsproblemen zu identifizieren:
   * Sortieren von Transaktionen nach aufsteigenden Apdex-Werten. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) bezieht sich auf die Benutzerzufriedenheit mit der Antwortzeit Ihrer Webanwendungen und -dienste. [Ein niedriger Apdex-Wert](/help/troubleshooting/miscellaneous/troubleshoot-performance-using-new-relic-on-magento-commerce.md#low_user_satisfaction) kann auf einen Engpass (eine Transaktion mit einer höheren Antwortzeit) hinweisen. Normalerweise ist es die Datenbank, Redis oder PHP. Anweisungen finden Sie unter New Relic [Anzeigen von Transaktionen mit der höchsten Apdex-Unzufriedenheit](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Sortieren Sie Transaktionen nach höchstem Durchsatz, langsamster durchschnittlicher Antwortzeit, zeitaufwendigsten und anderen Schwellenwerten. Anweisungen finden Sie unter New Relic [Suchen nach bestimmten Leistungsproblemen](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Wenn Sie immer noch Schwierigkeiten haben, die Quelle zu identifizieren, verwenden Sie die Infrastruktur-Seite des New Relic-APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/), um ressourcenintensive Dienste zu identifizieren. [ Anweisungen hierzu finden Sie auf der New Relic [Seite mit Hosts zur Infrastrukturüberwachung > Registerkarte &quot;Prozesse&quot;](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Wenn Sie die Quelle identifizieren, senden Sie SSH in die Umgebung, um weitere Untersuchungen durchzuführen. Anweisungen finden Sie unter [Cloud für Adobe Commerce > SSH in Ihrer Umgebung](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh) in unserer Entwicklerdokumentation.
1. Wenn Sie noch immer Schwierigkeiten haben, die Quelle zu identifizieren:
   * Überprüfen Sie aktuelle Trends, um Probleme mit kürzlich durchgeführten Code-Bereitstellungen oder Konfigurationsänderungen zu identifizieren (z. B. neue Kundengruppen und große Änderungen am Katalog). Es wird empfohlen, die letzten sieben Tage der Aktivität auf Korrelationen in Code-Bereitstellungen oder Änderungen zu überprüfen.
   * Überprüfen und deaktivieren Sie flache Kataloge. Anweisungen hierzu finden Sie unter [Langsame Leistung, langsame und langsame Kronen](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) in unserer Wissensdatenbank.
   * Wenn Sie vermuten, dass Sie einen DDoS-Angriff erleben, versuchen Sie, den Bot-Traffic zu blockieren. Anweisungen hierzu finden Sie in unserer Support-Wissensdatenbank unter [Wie Sie böswilligen Traffic für Adobe Commerce auf der Fastly-Ebene blockieren](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) .
1. Wenn das Problem vorübergehend erscheint, führen Sie Minderungsschritte wie eine Vergrößerung durch oder platzieren Sie die Site in den Wartungsmodus. Anweisungen finden Sie unter [Anfordern der temporären Größe](/help/how-to/general/how-to-request-temporary-magento-upsize.md) in unserer Support-Wissensdatenbank und [Installationshandbuch > Wartungsmodus aktivieren oder deaktivieren](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) in unserer Entwicklerdokumentation. Wenn die Upsize-Datei den normalen Betrieb der Site wiederherstellt, sollten Sie eine permanente Upsize anfordern (wenden Sie sich an Ihr Adobe Account-Team) oder versuchen, das Problem in Ihrer dedizierten Staging-Umgebung zu reproduzieren, indem Sie einen Lasttest durchführen und Abfragen optimieren oder Code verwenden, der den Druck auf Dienste verringert. Anweisungen finden Sie unter [Cloud für Adobe Commerce > Testbereitstellung > Laden und Stresstests](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) in unserer Entwicklerdokumentation.
