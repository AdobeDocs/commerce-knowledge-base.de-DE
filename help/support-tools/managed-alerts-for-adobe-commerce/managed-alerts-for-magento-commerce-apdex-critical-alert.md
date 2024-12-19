---
title: 'Verwaltete Warnhinweise für Adobe Commerce: Kritischer Warnhinweis von Apdex'
description: Dieser Artikel enthält Schritte zur Fehlerbehebung, wenn Sie einen kritischen Warnhinweis von Apdex für Adobe Commerce in New Relic erhalten. Der Apdex-Score misst die Zufriedenheit der Nutzer mit der Reaktionszeit von Web-Anwendungen und -Services. Sofortiges Handeln ist erforderlich, um das Problem zu beheben. Je nach ausgewähltem Benachrichtigungskanal für Warnhinweise sieht der Warnhinweis etwa wie folgt aus.
exl-id: b6d3d4f3-4abb-4285-8071-2b9fb06bfa3c
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 0%

---

# Verwaltete Warnhinweise für Adobe Commerce: Kritischer Warnhinweis von Apdex

Dieser Artikel enthält Schritte zur Fehlerbehebung, wenn Sie einen kritischen Warnhinweis von Apdex für Adobe Commerce in New Relic erhalten. Der Apdex-Score misst die Zufriedenheit der Nutzer mit der Reaktionszeit von Web-Anwendungen und -Services. Sofortiges Handeln ist erforderlich, um das Problem zu beheben. Je nach ausgewähltem Benachrichtigungskanal für Warnhinweise sieht der Warnhinweis etwa wie folgt aus.

![Kritischer APDEX-Warnhinweis](assets/apdex-critical-magento-managed.png){width="500"}

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur Pro Planarchitektur
* Starterplanarchitektur für Adobe Commerce auf Cloud-Infrastruktur

## Problem

Sie erhalten einen verwalteten Warnhinweis in New Relic, wenn Sie sich bei [Verwaltete Warnhinweise für Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) angemeldet haben und einer oder mehrere der Warnhinweisschwellen überschritten wurden. Diese Warnhinweise wurden von Adobe entwickelt, um Händlern mithilfe von Einblicken aus Support und Engineering einen Standardsatz zu bieten.

<u> **DO!** </u>

* Bricht jede geplante Bereitstellung ab, bis dieser Warnhinweis gelöscht wird.
* Setzen Sie Ihre Site sofort in den Wartungsmodus, wenn Ihre Site nicht mehr reagiert oder überhaupt nicht mehr reagiert. Anweisungen hierzu finden Sie [Installationshandbuch > Aktivieren oder Deaktivieren des ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)) in unserer Entwicklerdokumentation. Fügen Sie Ihre IP-Adresse der Liste der von der Steuer befreiten IP-Adressen hinzu, um sicherzustellen, dass Sie weiterhin zur Fehlerbehebung auf Ihre Website zugreifen können. Anweisungen hierzu finden Sie unter [Liste der ausgenommenen IP-Adressen verwalten](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt) in unserer Entwicklerdokumentation.

<u>**Tu&#39;s nicht!**</u>

* Starten Sie zusätzliche Marketing-Kampagnen, die zusätzliche Seitenansichten auf Ihre Site bringen können.
* Führen Sie Indexer oder zusätzliche Crons aus, was zu zusätzlichen Belastungen für CPU oder die Festplatte führen kann.
* Führen Sie alle wichtigen Verwaltungsaufgaben aus (z. B. Commerce-Admin, Datenimporte/-exporte).
* Leeren Sie den Cache.

Führen Sie die obigen Schritte aus, wenn Sie einen kritischen Warnhinweis erhalten haben, bevor Sie die Ursache des Warnhinweises behoben haben, kann dies dazu führen, dass Ihre Site nicht mehr reagiert, wenn Sie noch keinen Ausfall der Site feststellen.

## Lösung

Führen Sie diese Schritte aus, um die Ursache zu identifizieren und zu beheben.

>[!WARNING]
>
>Da es sich um einen kritischen Warnhinweis handelt, wird dringend empfohlen, **Schritt 1** auszuführen, bevor Sie versuchen, das Problem zu beheben (Schritt 2 ab).

1. Überprüfen, ob ein Adobe Commerce-Support-Ticket vorhanden ist. Anweisungen hierzu finden Sie unter [Support-Tickets nachverfolgen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) in unserer Support-Wissensdatenbank. Möglicherweise hat der Support eine New Relic-Schwellenwertwarnung erhalten, ein Ticket erstellt und die Arbeit an diesem Problem aufgenommen. Wenn kein Ticket vorhanden ist, erstellen Sie eines. Das Ticket sollte die folgenden Informationen enthalten:
   * Kontaktgrund: Wählen Sie „KRITISCHER New Relic-Warnhinweis empfangen“.
   * Beschreibung des Warnhinweises
   * [New Relic-Vorfall-Link](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Dies ist in Ihren [Verwaltete Warnhinweise für Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) enthalten.
1. Um die Ursache des Problems zu identifizieren, verwenden Sie die Seite Transaktion von [New Relic APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) um Transaktionen mit Leistungsproblemen zu identifizieren:
   * Sortieren Sie Transaktionen nach aufsteigenden Apdex-Werten. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) bezieht sich auf die Benutzerzufriedenheit hinsichtlich der Antwortzeit Ihrer Web-Anwendungen und -Services. Ein niedriger Apdex-Wert kann auf einen Engpass hinweisen (eine Transaktion mit einer höheren Antwortzeit). Normalerweise ist es die Datenbank, Redis oder PHP. Anweisungen hierzu finden Sie unter New Relic [Transaktionen mit höchster Apdex-Unzufriedenheit anzeigen](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction/#dissatisfaction).
   * Sortieren Sie Transaktionen nach dem höchsten Durchsatz, der langsamsten durchschnittlichen Antwortzeit, dem zeitaufwendigsten Wert und anderen Schwellenwerten. Anweisungen hierzu finden Sie unter New Relic [Spezifische Leistungsprobleme suchen](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Wenn Sie immer noch Schwierigkeiten haben, das Problem zu identifizieren, verwenden Sie die Seite Infrastruktur von New Relic APM.
1. Verwenden Sie die Seite „Infrastruktur“ von [New Relic APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) um ressourcenintensive Prozesse zu identifizieren. Anweisungen hierzu befinden sich auf der Seite New Relic [Überwachung von Hosts der Infrastruktur > Registerkarte Prozesse](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Wenn Services wie Redis oder MySQL die Hauptquelle für den Speicherverbrauch sind, versuchen Sie Folgendes:
   * Vergewissern Sie sich, dass Sie die neueste Version verwenden. Neuere Versionen können manchmal Speicherlecks beheben. Wenn Sie nicht die neueste Version verwenden, sollten Sie ein Upgrade in Erwägung ziehen. Anweisungen hierzu finden Sie unter [Cloud für Adobe Commerce > Services > Service ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) in unserer Entwicklerdokumentation.
   * Überprüfen Sie auf MySQL-Probleme wie lange laufende Abfragen, nicht definierte Primäre Schlüssel und doppelte Indizes. Anweisungen hierzu finden Sie unter [Häufigste Datenbankprobleme in Adobe Commerce auf Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) in unserer Entwicklerdokumentation.
   * Auf PHP-Probleme prüfen. Überprüfen Sie die ausgeführten Prozesse, indem Sie `ps aufx` in der CLI/Terminal ausführen. In der Terminal-Ausgabe werden Cron-Aufträge und -Prozesse angezeigt, die derzeit ausgeführt werden. Prüft die Ausgabe auf die Ausführungszeit der Prozesse. Wenn es eine Cron mit einer langen Ausführungszeit gibt, hängt die Cron möglicherweise. Informationen zu Schritten zur Fehlerbehebung finden Sie unter [Langsame Leistung, langsame und lang laufende ](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) und [Cron-Auftrag steckt im Status „Wird ausgeführt](/help/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.md) in unserer Support-Wissensdatenbank.

1. Sobald die Quelle identifiziert ist, SSH in die Umgebung, um weitere Untersuchungen durchzuführen. Anweisungen hierzu finden Sie unter [Cloud für Adobe Commerce > Technologien und Anforderungen > SSH in Ihrer Umgebung](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh) in unserer Entwicklerdokumentation.
1. Wenn Sie immer noch Schwierigkeiten haben, die Quelle zu identifizieren, überprüfen Sie die neuesten Trends, um Probleme mit aktuellen Code-Bereitstellungen oder Konfigurationsänderungen (z. B. neue Kundengruppen und große Änderungen am Katalog) zu identifizieren. Es wird empfohlen, die letzten sieben Tage der Aktivität auf Korrelationen in Code-Bereitstellungen oder -Änderungen zu überprüfen.
1. Wenn Sie innerhalb eines angemessenen Zeitraums keine Lösung finden können, fordern Sie eine Erweiterung an oder setzen Sie die Site in den Wartungsmodus, falls noch nicht geschehen. Anweisungen hierzu finden Sie unter [Wie man temp resize anfordert](/help/how-to/general/how-to-request-temporary-magento-upsize.md) in unserer Support-Wissensdatenbank und [Installationshandbuch > Wartungsmodus aktivieren oder deaktivieren](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) in unserer Entwicklerdokumentation.
1. Wenn die Aktualisierung zu einem normalen Betrieb der Website führt, sollten Sie eine permanente Aktualisierung anfordern (wenden Sie sich an Ihr Adobe-Account-Team) oder versuchen Sie, das Problem in Ihrem dedizierten Staging zu reproduzieren, indem Sie einen Lasttest durchführen und Abfragen optimieren oder Code verwenden, der den Druck auf die Services reduziert. Siehe [Cloud für Adobe Commerce > Testbereitstellung > Belastungs- und Stresstests](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) in unserer Entwicklerdokumentation.
