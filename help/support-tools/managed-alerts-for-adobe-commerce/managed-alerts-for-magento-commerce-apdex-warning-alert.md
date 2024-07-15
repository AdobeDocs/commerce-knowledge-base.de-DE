---
title: "Verwaltete Warnhinweise für Adobe Commerce: Warnhinweis für Index"
description: In diesem Artikel finden Sie Schritte zur Fehlerbehebung, die durchgeführt werden müssen, wenn Sie einen Warnhinweis für Adobe Commerce in New Relic erhalten. Der Apdex-Wert misst die Zufriedenheit der Benutzer mit der Reaktionszeit von Webanwendungen und -diensten. Um dieses Problem zu beheben, sind sofortige Maßnahmen erforderlich. Der Warnhinweis sieht je nach ausgewähltem Benachrichtigungskanal für Warnhinweise ungefähr wie folgt aus.
exl-id: 6e3f28ae-734b-468f-b6a5-c4f2edb1cb4b
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 3493214b468ac93dc938690495ea0a6bcf645a29
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 0%

---

# Verwaltete Warnhinweise für Adobe Commerce: Warnhinweis für Index

In diesem Artikel finden Sie Schritte zur Fehlerbehebung, die durchgeführt werden müssen, wenn Sie einen Warnhinweis für Adobe Commerce in New Relic erhalten. Der Apdex-Wert misst die Zufriedenheit der Benutzer mit der Reaktionszeit von Webanwendungen und -diensten. Um dieses Problem zu beheben, sind sofortige Maßnahmen erforderlich. Der Warnhinweis sieht je nach ausgewähltem Benachrichtigungskanal für Warnhinweise ungefähr wie folgt aus.

![apdex-Warnhinweis](assets/apdex-warning-magento-managed.png){width="500"}

## Betroffene Produkte und Versionen

* Adobe Commerce on Cloud Infrastructure Pro-Planarchitektur
* Adobe Commerce zur Starter-Planarchitektur der Cloud-Infrastruktur

## Problem

Sie erhalten einen Warnhinweis, der in New Relic verwaltet wird, wenn Sie bis zu [Warnhinweise für Adobe Commerce verwalten](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) angemeldet haben und mindestens eine der Warnschwellen überschritten wurde. Diese Warnhinweise wurden von Adobe entwickelt, um Händlern mithilfe von Einblicken aus Support und Engineering einen Standardsatz zu liefern.

<u> **Do!** </u>

* Beenden Sie alle geplanten Implementierungen, bis dieser Warnhinweis gelöscht ist.
* Setzen Sie Ihre Site sofort in den Wartungsmodus, wenn Ihre Site vollständig oder gar nicht reagiert. Anweisungen finden Sie unter [Installationshandbuch > Wartungsmodus aktivieren oder deaktivieren](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) in unserer Entwicklerdokumentation. Stellen Sie sicher, dass Sie Ihre IP-Adresse zur Liste der ausgenommenen IP-Adressen hinzufügen, um sicherzustellen, dass Sie weiterhin auf Ihre Website zugreifen können, um die Fehlerbehebung durchzuführen. Anweisungen finden Sie unter [Verwalten der Liste der ausgenommenen IP-Adressen](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) in unserer Entwicklerdokumentation.

<u>**Nicht!**</u>

* Starten Sie zusätzliche Marketing-Kampagnen, die zusätzliche Seitenansichten zu Ihrer Site bringen können.
* Führen Sie Indexer oder zusätzliche Crons aus, die zusätzliche Belastungen für CPU oder Festplatte verursachen können.
* Führen Sie alle wichtigen Verwaltungsaufgaben aus (z. B. Commerce-Administrator, Datenimport/-export).
* Löschen Sie den Cache.

## Lösung

Führen Sie diese Schritte aus, um die Ursache zu identifizieren und zu beheben.

1. Um die Ursache des Problems zu ermitteln, verwenden Sie die Transaktionsseite des New Relic-APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems), um Transaktionen mit Leistungsproblemen zu identifizieren:[
   * Sortieren von Transaktionen nach aufsteigenden Apdex-Werten. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) bezieht sich auf die Benutzerzufriedenheit mit der Antwortzeit Ihrer Webanwendungen und -dienste. Ein [niedriger Apdex-Wert](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) kann auf einen Engpass (eine Transaktion mit einer höheren Antwortzeit) hinweisen. Normalerweise ist es die Datenbank, Redis oder PHP. Anweisungen finden Sie unter New Relic [Anzeigen von Transaktionen mit der höchsten Apdex-Unzufriedenheit](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Sortieren Sie Transaktionen nach dem höchsten Durchsatz, der langsamsten durchschnittlichen Antwortzeit, dem zeitaufwendigsten und anderen Schwellenwerten. Anweisungen finden Sie unter New Relic [Suchen nach bestimmten Leistungsproblemen](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Verwenden Sie die Infrastrukturseite des New Relic-APM ](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/), um ressourcenintensive Prozesse zu identifizieren. [ Anweisungen hierzu finden Sie auf der New Relic [Seite mit Hosts zur Infrastrukturüberwachung > Registerkarte &quot;Prozesse&quot;](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Wenn Dienste wie Redis oder MySQL die Hauptquelle für den Speicherverbrauch sind, versuchen Sie Folgendes:
   * Vergewissern Sie sich, dass Sie die neueste Version verwenden. Neuere Versionen können manchmal Speicherlecks beheben. Wenn Sie nicht die neueste Version verwenden, sollten Sie ein Upgrade in Erwägung ziehen. Anweisungen finden Sie unter [Cloud für Adobe Commerce > Dienste > Dienste ändern](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) in unserer Entwicklerdokumentation.
1. Wenn das Problem nicht durch Service-Versionen verursacht wird:
   * Suchen Sie nach anderen MySQL-Problemen wie langwierigen Abfragen, nicht definierten Primären Schlüsseln und doppelten Indizes. Anweisungen finden Sie unter [Die häufigsten Datenbankprobleme in Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) in unserer Support-Wissensdatenbank.
   * Suchen Sie nach anderen PHP-Problemen. Überprüfen Sie die ausgeführten Prozesse, indem Sie im CLI/Terminal `ps aufx` ausführen. In der Terminal-Ausgabe sehen Sie Cron-Aufträge und -Prozesse, die derzeit ausgeführt werden. Überprüfen Sie die Ausgabe auf die Ausführungszeit der Prozesse. Wenn es einen Cron mit einer langen Ausführungszeit gibt, hängt der Cron möglicherweise. Informationen zur Fehlerbehebung finden Sie unter [Langsame Leistung, langsame und lange laufende Crons](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) und [Cron-Auftrag stecken im Status &quot;Wird ausgeführt&quot;](/help/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.md) in unserer Support-Wissensdatenbank.
1. Sobald eine potenzielle Quelle des Problems ermittelt ist, kann SSH in die Umwelt eindringen, um weitere Untersuchungen durchzuführen. Anweisungen finden Sie unter [Cloud für Adobe Commerce > Technologien und Anforderungen > SSH in Ihrer Umgebung](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh) in unserer Entwicklerdokumentation.
1. Wenn Sie nach wie vor Schwierigkeiten haben, die Quelle zu identifizieren, überprüfen Sie aktuelle Trends, um Probleme mit kürzlich durchgeführten Code-Bereitstellungen oder Konfigurationsänderungen zu identifizieren (z. B. neue Kundengruppen und große Änderungen am Katalog). Es wird empfohlen, die letzten sieben Tage der Aktivität auf Korrelationen in Code-Bereitstellungen oder Änderungen zu überprüfen.
1. Wenn Sie innerhalb einer angemessenen Zeit keine Lösung finden können, fordern Sie eine Aktualisierung an oder platzieren Sie die Site in den Wartungsmodus, falls Sie dies noch nicht getan haben. Anweisungen finden Sie unter [Anfordern der temporären Größe](/help/how-to/general/how-to-request-temporary-magento-upsize.md) in unserer Support-Wissensdatenbank und [Installationshandbuch > Wartungsmodus aktivieren oder deaktivieren](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) in unserer Entwicklerdokumentation.
1. Wenn der [upsize](/help/how-to/general/how-to-request-temporary-magento-upsize.md) die Site wieder in den normalen Betrieb einstellt, sollten Sie eine dauerhafte Upsize-Anforderung anfordern (kontaktieren Sie Ihr Adobe Account-Team) oder versuchen, das Problem in Ihrem dedizierten Staging zu reproduzieren, indem Sie einen Lasttest durchführen und Abfragen optimieren oder Code, der den Druck auf Dienste verringert. Weitere Informationen finden Sie in unserer Entwicklerdokumentation unter [Cloud für Adobe Commerce > Testbereitstellung > Laden und Stresstests](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) .
