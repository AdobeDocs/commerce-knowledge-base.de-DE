---
title: 'Verwaltete Warnhinweise für Adobe Commerce: Warnhinweis für CPU'
description: Dieser Artikel enthält Schritte zur Fehlerbehebung, wenn Sie einen CPU-Warnhinweis für Adobe Commerce in New Relic erhalten. Sofortiges Handeln ist erforderlich, um das Problem zu beheben. Je nach ausgewähltem Benachrichtigungskanal für Warnhinweise sieht der Warnhinweis etwa wie folgt aus.
exl-id: 03686684-3b7e-430a-a05a-a96f38345322
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 0%

---

# Verwaltete Warnhinweise für Adobe Commerce: Warnhinweis für CPU

Dieser Artikel enthält Schritte zur Fehlerbehebung, wenn Sie einen CPU-Warnhinweis für Adobe Commerce in New Relic erhalten. Sofortiges Handeln ist erforderlich, um das Problem zu beheben. Je nach ausgewähltem Benachrichtigungskanal für Warnhinweise sieht der Warnhinweis etwa wie folgt aus.

![CPU-Warnhinweis](assets/cpu-warning-magento-managed.png){width="500"}

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur Pro Planarchitektur

## Problem

Sie erhalten einen Warnhinweis in New Relic, wenn Sie sich bei [Verwaltete Warnhinweise für Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) angemeldet haben und einer oder mehrere der Warnhinweisschwellen überschritten wurden. Diese Warnhinweise wurden von Adobe entwickelt, um Kunden mithilfe von Einblicken aus Support und Engineering einen Standardsatz zu bieten.

<u> **DO!** </u>

* Bricht jede geplante Bereitstellung ab, bis dieser Warnhinweis gelöscht wird.
* Setzen Sie Ihre Site sofort in den Wartungsmodus, wenn Ihre Site vollständig nicht reagiert. Anweisungen hierzu finden Sie [Installationshandbuch > Aktivieren oder Deaktivieren des ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)) in unserer Entwicklerdokumentation. Fügen Sie Ihre IP-Adresse der Liste der von der Steuer befreiten IP-Adressen hinzu, um sicherzustellen, dass Sie weiterhin zur Fehlerbehebung auf Ihre Website zugreifen können. Anweisungen hierzu finden Sie unter [Liste der ausgenommenen IP-Adressen verwalten](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt) in unserer Entwicklerdokumentation.

<u>**Tu&#39;s nicht!**</u>

* Starten Sie zusätzliche Marketing-Kampagnen, die zusätzliche Seitenansichten auf Ihre Site bringen können.
* Führen Sie Indexer oder zusätzliche Crons aus, was zu zusätzlichen Belastungen für CPU oder die Festplatte führen kann.
* Führen Sie alle wichtigen administrativen Aufgaben aus (z. B. Commerce-Admin, Datenimporte/-exporte).
* Leeren Sie den Cache.

## Lösung

Führen Sie diese Schritte aus, um die Ursache zu identifizieren und zu beheben.

1. Verwenden Sie die Seite Transaktion von [New Relic APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) um Transaktionen mit Leistungsproblemen zu identifizieren:
   * Sortieren Sie Transaktionen nach aufsteigenden Apdex-Werten. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) bezieht sich auf die Benutzerzufriedenheit hinsichtlich der Antwortzeit Ihrer Web-Anwendungen und -Services. [Ein niedriger Apdex-Wert](/help/troubleshooting/miscellaneous/troubleshoot-performance-using-new-relic-on-magento-commerce.md#low_user_satisfaction) kann auf einen Engpass hinweisen (eine Transaktion mit einer höheren Antwortzeit). Normalerweise ist es die Datenbank, Redis oder PHP. Anweisungen hierzu finden Sie unter New Relic [Transaktionen mit höchster Apdex-Unzufriedenheit anzeigen](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Sortieren Sie Transaktionen nach dem höchsten Durchsatz, der langsamsten durchschnittlichen Reaktionszeit, dem zeitaufwendigsten Wert und anderen Schwellenwerten. Anweisungen hierzu finden Sie unter New Relic [Spezifische Leistungsprobleme suchen](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Wenn Sie immer noch versuchen, die Quelle zu identifizieren, verwenden Sie die Seite Infrastruktur von [New Relic APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) um ressourcenintensive Services zu identifizieren. Anweisungen hierzu befinden sich auf der Seite New Relic [Überwachung von Hosts der Infrastruktur > Registerkarte Prozesse](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Wenn Sie die Quelle identifizieren, SSH in die Umgebung, um weiter zu untersuchen. Anweisungen hierzu finden Sie unter [Cloud für Adobe Commerce > SSH in Ihre Umgebung](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh) in unserer Entwicklerdokumentation.
1. Wenn Sie immer noch damit kämpfen, die Quelle zu identifizieren:
   * Überprüfen Sie die neuesten Trends, um Probleme mit aktuellen Code-Bereitstellungen oder Konfigurationsänderungen zu identifizieren (z. B. neue Kundengruppen und große Änderungen am Katalog). Es wird empfohlen, die letzten sieben Tage der Aktivität auf Korrelationen in Code-Bereitstellungen oder -Änderungen zu überprüfen.
   * Erwägen Sie, nach flachen Katalogen zu suchen und sie zu deaktivieren. Anweisungen hierzu finden Sie unter [Langsame Leistung, langsame und lang laufende Crons](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) in unserer Support-Wissensdatenbank.
   * Wenn Sie einen DDoS-Angriff vermuten, versuchen Sie, Bot-Traffic zu blockieren. Anweisungen hierzu finden Sie unter [Wie Sie bösartigen Traffic für Adobe Commerce auf Fastly-Ebene blockieren](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) in unserer Support-Wissensdatenbank.
1. Wenn das Problem vorübergehend zu sein scheint, führen Sie Schritte zur Risikominderung durch, z. B. eine Vergrößerung oder setzen Sie die Site in den Wartungsmodus. Anweisungen hierzu finden Sie unter [Wie man temp resize anfordert](/help/how-to/general/how-to-request-temporary-magento-upsize.md) in unserer Support-Wissensdatenbank und [Installationshandbuch > Wartungsmodus aktivieren oder deaktivieren](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) in unserer Entwicklerdokumentation. Wenn die Aktualisierung zu einem normalen Betrieb der Site führt, fordern Sie eine permanente Aktualisierung an (wenden Sie sich an Ihr Adobe-Account-Team) oder versuchen Sie, das Problem in Ihrem dedizierten Staging zu reproduzieren, indem Sie einen Lasttest durchführen und Abfragen optimieren oder Code verwenden, der den Druck auf die Services reduziert. Anweisungen hierzu finden Sie unter [Cloud für Adobe Commerce > Testbereitstellung > Belastungs- und Stresstests](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) in unserer Entwicklerdokumentation.
