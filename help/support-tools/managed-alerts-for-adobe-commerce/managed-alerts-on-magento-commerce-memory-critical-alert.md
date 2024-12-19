---
title: 'Verwaltete Warnhinweise auf Adobe Commerce: Kritischer Warnhinweis zum Arbeitsspeicher'
description: Dieser Artikel enthält Schritte zur Fehlerbehebung, wenn Sie in New Relic einen kritischen Warnhinweis zu Speicher für Adobe Commerce erhalten. Sofortiges Handeln ist erforderlich, um das Problem zu beheben. Je nach ausgewähltem Benachrichtigungskanal für Warnhinweise sieht der Warnhinweis etwa wie folgt aus.
exl-id: feed7998-c50b-4cbf-a92d-cbfc65745a1c
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 0%

---

# Verwaltete Warnhinweise auf Adobe Commerce: Kritischer Warnhinweis zum Arbeitsspeicher

Dieser Artikel enthält Schritte zur Fehlerbehebung, wenn Sie in New Relic einen kritischen Warnhinweis zu Speicher für Adobe Commerce erhalten. Sofortiges Handeln ist erforderlich, um das Problem zu beheben. Je nach ausgewähltem Benachrichtigungskanal für Warnhinweise sieht der Warnhinweis etwa wie folgt aus.

![Kritischer Warnhinweis auf Festplatte](assets/memory-critical-magento-managed.png){width="500"}

## Betroffene Produkte und Versionen

Alle Versionen von Adobe Commerce auf Cloud-Infrastruktur Pro planen Architektur.

## Problem

Sie erhalten einen verwalteten Warnhinweis in New Relic, wenn Sie sich bei [Verwaltete Warnhinweise für Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) angemeldet haben und einer oder mehrere der Warnhinweisschwellen überschritten wurden. Diese Warnhinweise wurden von Adobe entwickelt, um Kunden mithilfe von Einblicken aus Support und Engineering einen Standardsatz zu bieten.

<u> **DO!** </u>

* Alle geplanten Bereitstellungen abbrechen, bis dieser Warnhinweis gelöscht wird
* Setzen Sie Ihre Site sofort in den Wartungsmodus, wenn Ihre Site nicht mehr reagiert oder überhaupt nicht mehr reagiert. Anweisungen hierzu finden Sie [Installationshandbuch > Wartungsmodus aktivieren oder deaktivieren](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) in unserer Entwicklerdokumentation. Fügen Sie Ihre IP-Adresse der Liste der von der Steuer befreiten IP-Adressen hinzu, um sicherzustellen, dass Sie weiterhin zur Fehlerbehebung auf Ihre Website zugreifen können. Anweisungen hierzu finden Sie unter [Verwalten der Liste ausgenommener IP-Adressen](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt) in unserer Entwicklerdokumentation.

<u>**Tu&#39;s nicht!**</u>

* Starten Sie zusätzliche Marketing-Kampagnen, die zusätzliche Seitenansichten auf Ihre Site bringen können.
* Führen Sie Indexer oder zusätzliche Crons aus, was zu zusätzlichen Belastungen für CPU oder die Festplatte führen kann.
* Führen Sie alle wichtigen administrativen Aufgaben aus (z. B. Commerce-Admin, Datenimporte/-exporte).
* Leeren Sie den Cache.

Ihre Site kann nicht mehr reagieren (wenn Sie noch keinen Ausfall der Site feststellen), wenn Sie eine der „Nicht reagieren“-Aktionen durchführen, bevor Sie die Ursache des Warnhinweises untersucht und behoben haben.

## Lösung

Führen Sie diese Schritte aus, um die Ursache zu identifizieren und zu beheben.

>[!WARNING]
>
>Da es sich um einen kritischen Warnhinweis handelt, wird dringend empfohlen, **Schritt 1** auszuführen, bevor Sie versuchen, das Problem zu beheben (Schritt 2 ab).

1. Überprüfen, ob ein Adobe Commerce-Support-Ticket vorhanden ist. Anweisungen hierzu finden Sie [Support-Tickets ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) unserer Support-Wissensdatenbank verfolgen. Möglicherweise hat der Support bereits eine New Relic-Schwellenwertwarnung erhalten, ein Ticket erstellt und mit der Bearbeitung des Problems begonnen. Wenn kein Ticket vorhanden ist, erstellen Sie eines. Das Ticket sollte die folgenden Informationen enthalten:
   * Kontaktgrund: Wählen Sie „KRITISCHER New Relic-Warnhinweis empfangen“
   * Beschreibung der Warnmeldung
   * [New Relic-Vorfall-Link](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Dies ist in Ihren [Verwaltete Warnhinweise für Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) enthalten.

1. Verwenden Sie die Seite „Infrastruktur“ von [New Relic APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/), um die speicherintensivsten Prozesse zu identifizieren. Anweisungen hierzu befinden sich auf der Seite New Relic [Überwachung von Hosts der Infrastruktur > Registerkarte Prozesse](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes):
   * Wenn Services wie Redis, MySQL oder PHP die wichtigsten Quellen für den Speicherverbrauch sind, versuchen Sie Folgendes:
1. Vergewissern Sie sich, dass Sie die neuesten Versionen verwenden. Neuere Versionen können manchmal Speicherlecks beheben. Wenn Sie nicht die neueste Version verwenden, sollten Sie ein Upgrade in Erwägung ziehen. Anweisungen hierzu finden Sie unter [Adobe Commerce in Cloud-Infrastruktur > Services > Service ändern](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) in unserer Entwicklerdokumentation.
1. Wenn das Problem mit dem Service nicht versionsbezogen ist, versuchen Sie Folgendes:
1. **MySQL**: Überprüfen Sie, ob Probleme wie lange laufende Abfragen, nicht definierte Primäre Schlüssel und doppelte Indizes auftreten. Anweisungen hierzu finden Sie unter [Häufigste Datenbankprobleme in Adobe Commerce auf Cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) in unserer Support-Wissensdatenbank.
1. **Redis**: Wenn Redis eine der Hauptquellen für den Speicherverbrauch ist, [ Sie ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
1. **PHP**: Wenn PHP eine der Hauptquellen für den Speicherverbrauch ist, überprüfen Sie die laufenden Prozesse, indem Sie `ps aufx` in der CLI/Terminal ausführen. In der Terminal-Ausgabe werden Cron-Aufträge und -Prozesse angezeigt, die derzeit ausgeführt werden. Prüft die Ausgabe auf die Ausführungszeit der Prozesse. Wenn es eine Cron mit einer langen Ausführungszeit gibt, hängt die Cron möglicherweise. Informationen zu Schritten zur Fehlerbehebung finden Sie unter [Langsame Leistung, langsame und lang laufende Crons](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) und [Cron-Auftrag steckt im Status „Wird ausgeführt](https://support.magento.com/hc/en-us/articles/360033099451) in unserer Support-Wissensdatenbank.
1. Wenn Sie immer noch versuchen, die Ursache des Problems zu identifizieren, verwenden Sie die Seite Transaktion von [New Relic APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) um Transaktionen mit Leistungsproblemen zu identifizieren:
   * Sortieren Sie Transaktionen nach aufsteigenden Apdex-Werten. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) bezieht sich auf die Benutzerzufriedenheit hinsichtlich der Antwortzeit Ihrer Web-Anwendungen und -Services. Ein [niedriger Apdex-Wert](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) kann auf einen Engpass hinweisen (eine Transaktion mit einer höheren Antwortzeit). Normalerweise ist es die Datenbank, Redis oder PHP. Anweisungen hierzu finden Sie unter New Relic [Transaktionen mit höchster Apdex-Unzufriedenheit anzeigen](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Sortieren Sie Transaktionen nach dem höchsten Durchsatz, der langsamsten durchschnittlichen Antwortzeit, dem zeitaufwendigsten Wert und anderen Schwellenwerten. Anweisungen hierzu finden Sie unter New Relic [Spezifische Leistungsprobleme suchen](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Wenn Sie immer noch Schwierigkeiten haben, das Problem zu identifizieren, verwenden Sie die Seite Infrastruktur von New Relic APM.
1. Wenn Sie die Ursache für den erhöhten Speicherverbrauch nicht identifizieren können, überprüfen Sie die neuesten Trends, um Probleme mit aktuellen Code-Bereitstellungen oder Konfigurationsänderungen (z. B. neue Kundengruppen und große Änderungen am Katalog) zu identifizieren. Es wird empfohlen, die letzten 7 Tage der Aktivität auf Korrelationen in Code-Bereitstellungen oder -Änderungen zu überprüfen.
1. Wenn die oben genannten Methoden Ihnen nicht helfen, die Ursache und/oder Lösung innerhalb einer angemessenen Zeit zu finden, fordern Sie eine Erweiterung an oder setzen Sie die Site in den Wartungsmodus, falls Sie dies noch nicht getan haben. Anweisungen hierzu finden [ in unserer Support](/help/how-to/general/how-to-request-temporary-magento-upsize.md)Wissensdatenbank unter „Anfordern der temporären Größe“ und [Installationshandbuch > Wartungsmodus aktivieren oder deaktivieren](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) in unserer Entwicklerdokumentation.
1. Wenn die Aktualisierung zu einem normalen Betrieb der Website führt, sollten Sie eine permanente Aktualisierung anfordern (wenden Sie sich an Ihr Adobe-Account-Team) oder versuchen Sie, das Problem in Ihrem dedizierten Staging zu reproduzieren, indem Sie einen Lasttest durchführen und Abfragen optimieren oder Code verwenden, der den Druck auf die Services reduziert. Siehe [Adobe Commerce in der Cloud-Infrastruktur > Testbereitstellung > Belastungs- und ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) in unserer Entwicklerdokumentation.
