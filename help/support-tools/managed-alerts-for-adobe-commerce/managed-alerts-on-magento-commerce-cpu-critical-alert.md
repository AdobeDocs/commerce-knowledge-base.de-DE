---
title: 'Verwaltete Warnhinweise in Adobe Commerce: Kritischer Warnhinweis in CPU'
description: Dieser Artikel enthält Schritte zur Fehlerbehebung, wenn Sie einen kritischen Warnhinweis von CPU für Adobe Commerce in New Relic erhalten. Sofortiges Handeln ist erforderlich, um das Problem zu beheben. Je nach ausgewähltem Benachrichtigungskanal für Warnhinweise sieht der Warnhinweis etwa wie folgt aus.
exl-id: 45b8ced0-b12f-428b-9838-2a9c26b9874b
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 0%

---

# Verwaltete Warnhinweise in Adobe Commerce: Kritischer Warnhinweis in CPU

Dieser Artikel enthält Schritte zur Fehlerbehebung, wenn Sie einen kritischen Warnhinweis von CPU für Adobe Commerce in New Relic erhalten. Sofortiges Handeln ist erforderlich, um das Problem zu beheben. Je nach ausgewähltem Benachrichtigungskanal für Warnhinweise sieht der Warnhinweis etwa wie folgt aus.

![Kritischer Warnhinweis auf Festplatte](assets/cpu-critical-magento-managed.png){width="500"}

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur Pro Planarchitektur

## Problem

Sie erhalten einen verwalteten Warnhinweis in New Relic, wenn Sie sich bei [Verwaltete Warnhinweise für Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) angemeldet haben und einer oder mehrere der Warnhinweisschwellen überschritten wurden. Diese Warnhinweise wurden von Adobe Commerce entwickelt, um Kundinnen und Kunden mithilfe von Einblicken aus Support und Engineering einen Standardsatz zu bieten.

<u>**DO!**</u>:

* Bricht jede geplante Bereitstellung ab, bis dieser Warnhinweis gelöscht wird.
* Setzen Sie Ihre Site sofort in den Wartungsmodus, wenn Ihre Site nicht mehr reagiert oder überhaupt nicht mehr reagiert. Anweisungen hierzu finden Sie [Installationshandbuch > Aktivieren oder Deaktivieren des ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)) in unserer Entwicklerdokumentation. Fügen Sie Ihre IP-Adresse der Liste der von der Steuer befreiten IP-Adressen hinzu, um sicherzustellen, dass Sie weiterhin zur Fehlerbehebung auf Ihre Website zugreifen können. Anweisungen hierzu finden Sie unter [Liste der ausgenommenen IP-Adressen verwalten](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt) in unserer Entwicklerdokumentation.

<u>**Nicht tun!**</u>:

* Starten Sie zusätzliche Marketing-Kampagnen, die zusätzliche Seitenansichten auf Ihre Site bringen können.
* Führen Sie Indexer oder zusätzliche Crons aus, was zu zusätzlichen Belastungen für die CPU oder die Festplatte führen kann.
* Führen Sie alle wichtigen Verwaltungsaufgaben aus (z. B. Commerce-Admin, Datenimporte/-exporte).
* Leeren Sie den Cache.

Ihre Site reagiert möglicherweise nicht mehr (wenn Sie noch keinen Ausfall der Site feststellen), wenn Sie eine der Aktionen „Nicht ausführen“ ausführen, bevor Sie die Ursache des Warnhinweises untersucht und behoben haben.

## Lösung

Führen Sie diese Schritte aus, um die Ursache zu identifizieren und zu beheben.

>[!WARNING]
>
>Da es sich um einen kritischen Warnhinweis handelt, wird dringend empfohlen, **Schritt 1** auszuführen, bevor Sie versuchen, das Problem zu beheben (Schritt 2 ab).

Überprüfen Sie, ob das Adobe Commerce-Support-Ticket vorhanden ist. Anweisungen hierzu finden Sie unter [Support-Tickets nachverfolgen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) in unserer Support-Wissensdatenbank. Möglicherweise hat der Support eine New Relic-Schwellenwertwarnung erhalten, ein Ticket erstellt und die Arbeit an dem Problem begonnen. Wenn kein Ticket vorhanden ist, erstellen Sie eines. Das Ticket sollte die folgenden Informationen enthalten:

1. Kontaktgrund: Wählen Sie „KRITISCHER New Relic-Warnhinweis empfangen“.
1. Beschreibung des Warnhinweises
1. [New Relic-Vorfall-Link](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Dies ist in Ihren [Verwaltete Warnhinweise für Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) enthalten.
1. Verwenden Sie die Seite Transaktion von [New Relic APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) um Transaktionen mit Leistungsproblemen zu identifizieren:
   * Sortieren Sie Transaktionen nach aufsteigenden Apdex-Werten. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) bezieht sich auf die Benutzerzufriedenheit hinsichtlich der Antwortzeit Ihrer Web-Anwendungen und -Services. Ein [niedriger Apdex-Wert](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) kann auf einen Engpass hinweisen (eine Transaktion mit einer höheren Antwortzeit). Normalerweise ist es mit der Datenbank, Redis oder PHP verbunden. Anweisungen hierzu finden Sie unter New Relic [Transaktionen mit höchster Apdex-Unzufriedenheit anzeigen](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Sortieren Sie Transaktionen nach dem höchsten Durchsatz, der langsamsten durchschnittlichen Reaktionszeit, dem zeitaufwendigsten Wert und anderen Schwellenwerten. Anweisungen hierzu finden Sie unter New Relic [Spezifische Leistungsprobleme suchen](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Wenn Sie immer noch Schwierigkeiten haben, die Quelle zu identifizieren, verwenden Sie die Seite Infrastruktur von [New Relic APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page) um ressourcenintensive Services zu identifizieren. Anweisungen hierzu befinden sich auf der Seite New Relic [Überwachung von Hosts der Infrastruktur > Registerkarte Prozesse](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Wenn Sie die Quelle identifizieren, SSH in die Umgebung, um weiter zu untersuchen. Anweisungen hierzu finden Sie unter [SSH in Ihre Umgebung für Adobe Commerce auf Cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) in unserer Entwicklerdokumentation.
1. Wenn Sie immer noch damit kämpfen, die Quelle zu identifizieren:
   * Überprüfen Sie die neuesten Trends, um Probleme mit aktuellen Code-Bereitstellungen oder Konfigurationsänderungen zu identifizieren (z. B. neue Kundengruppen und große Änderungen am Katalog). Es wird empfohlen, die letzten sieben Tage der Aktivität auf Korrelationen in Code-Bereitstellungen oder -Änderungen zu überprüfen.
   * Erwägen Sie, nach flachen Katalogen zu suchen und sie zu deaktivieren. Anweisungen hierzu finden Sie unter [Langsame Leistung, langsame und lang laufende Crons](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) in unserer Support-Wissensdatenbank.
   * Wenn Sie einen DDoS-Angriff vermuten, versuchen Sie, Bot-Traffic zu blockieren. Anweisungen hierzu finden Sie unter [Wie Sie bösartigen Traffic für Adobe Commerce in der Cloud-Infrastruktur auf Fastly-Ebene blockieren](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) in unserer Support-Wissensdatenbank.
1. Wenn das Problem vorübergehend zu sein scheint, führen Sie Schritte zur Risikominderung durch, z. B. eine Vergrößerung oder setzen Sie die Site in den Wartungsmodus. Anweisungen hierzu finden Sie unter [Wie man temp resize anfordert](/help/how-to/general/how-to-request-temporary-magento-upsize.md) in unserer Support-Wissensdatenbank und [Installationshandbuch > Wartungsmodus aktivieren oder deaktivieren](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) in unserer Entwicklerdokumentation. Wenn die Aktualisierung zu einem normalen Betrieb der Site führt, fordern Sie eine permanente Aktualisierung an (wenden Sie sich an Ihr Adobe-Account-Team) oder versuchen Sie, das Problem in Ihrem dedizierten Staging zu reproduzieren, indem Sie einen Lasttest durchführen und Abfragen oder Code optimieren, der den Druck auf die Services reduziert. Anweisungen hierzu finden Sie unter [Testbereitstellung > Belastungs- und Belastungstests](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) in unserer Entwicklerdokumentation für Adobe Commerce in Cloud-Infrastrukturen.
