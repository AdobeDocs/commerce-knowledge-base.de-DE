---
title: 'Verwaltete Warnhinweise in Adobe Commerce: MariaDB-Warnhinweise'
description: 'Dieser Artikel enthält Schritte zur Fehlerbehebung, wenn Sie in New Relic MariaDB-Warnhinweise für Adobe Commerce erhalten. Die MariaDB-Warnhinweise überwachen eine hohe Abfragelast sowie übermäßige DML-Abfragen (Data Manipulation Language). Beides kann zu einem schlechteren Benutzererlebnis oder sogar zu Ausfallzeiten führen. Sie können vier Arten von Warnhinweisen erhalten:'
exl-id: 707e20e0-faba-4bcd-884c-b54568787442
feature: Cache, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# Verwaltete Warnhinweise in Adobe Commerce: MariaDB-Warnhinweise

Dieser Artikel enthält Schritte zur Fehlerbehebung, wenn Sie in New Relic MariaDB-Warnhinweise für Adobe Commerce erhalten. Die MariaDB-Warnhinweise überwachen eine hohe Abfragelast sowie übermäßige DML-Abfragen (Data Manipulation Language). Beides kann zu einem schlechteren Benutzererlebnis oder sogar zu Ausfallzeiten führen. Sie können vier Arten von Warnhinweisen erhalten:

* Warnung zu DML-Abfragen
* Wichtige DML-Abfragen

## **Betroffene Produkte und Versionen**

Adobe Commerce auf Cloud-Infrastruktur Pro Planarchitektur

## Problem

Sie erhalten einen verwalteten Warnhinweis in New Relic, wenn Sie sich bei [Verwaltete Warnhinweise für Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) angemeldet haben und einer oder mehrere der Warnhinweisschwellen überschritten wurden. Diese Warnhinweise wurden von Adobe entwickelt, um Kunden mithilfe von Einblicken aus Support und Engineering einen Standardsatz zu bieten.

**Do!**

* Bricht jede geplante Bereitstellung ab, bis dieser Warnhinweis gelöscht wird.
* Setzen Sie Ihre Site sofort in den Wartungsmodus, wenn Ihre Site nicht mehr reagiert oder überhaupt nicht mehr reagiert. Anweisungen hierzu finden Sie [Installationshandbuch > Wartungsmodus aktivieren oder deaktivieren](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) in unserer Entwicklerdokumentation. Fügen Sie Ihre IP-Adresse der Liste der von der Steuer befreiten IP-Adressen hinzu, um sicherzustellen, dass Sie weiterhin zur Fehlerbehebung auf Ihre Website zugreifen können. Anweisungen hierzu finden Sie unter [Liste der ausgenommenen IP-Adressen verwalten](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt).
* Beenden Sie alle Skripte, z. B. Importe, die die Ursache des Warnhinweises sein könnten, wenn die Site-Leistung beeinträchtigt ist.

**Tu&#39;s nicht!**

* Führen Sie Indexer oder zusätzliche Crons aus, die zusätzlichen Stress auf MariaDB verursachen können.
* Führen Sie alle wichtigen administrativen Aufgaben aus (z. B. Commerce-Admin, Datenimporte/-exporte).
* Leeren Sie den Cache.

## Lösung

**DML-Abfragen (Abfragen, die die Datenbank mithilfe von UPDATE, INSERT und DELETE ändern)**

Wenn Sie einen kritischen Warnhinweis für XML-Abfragen erhalten, beginnen Sie in Schritt 1. Wenn Sie einen Warnhinweis zu DML-Abfragen erhalten, beginnen Sie in Schritt 2.

1. Überprüfen, ob ein Adobe Commerce-Support-Ticket vorhanden ist. Anweisungen hierzu finden Sie in unserer Wissensdatenbank [Support-Tickets ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets). Möglicherweise hat der Support eine New Relic-Schwellenwertwarnung erhalten, ein Ticket erstellt und die Arbeit an diesem Problem aufgenommen. Wenn kein Ticket vorhanden ist, erstellen Sie eines. Das Ticket sollte die folgenden Informationen enthalten:
1. Kontaktgrund: Wählen Sie &quot;New Relic MariaDB-Warnhinweis empfangen“.
1. Beschreibung des Warnhinweises
1. [New Relic-Vorfall-Link](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Dies ist in Ihren [Verwaltete Warnhinweise für Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) enthalten.
1. Um die Ursache des Problems zu identifizieren, versuchen Sie, die XML-Abfragen zu identifizieren:
1. Überprüfen Sie Ihre Datenbankvorgänge mithilfe der Schritte auf der Seite New Relic [Seiten der APM-Benutzeroberfläche > Überwachung > Datenbanken](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time) .
1. Sortieren Sie nach CALL COUNT, dann OPERATION. Überprüfen Sie die Vorgänge INSERT, DELETE und UPDATE.
1. Achten Sie auf hohe Durchschnitte.
1. Durchklicken, um Aufrufe von Datenbankvorgängen zu finden. Dadurch werden Transaktionen identifiziert, die diese Abfrage nach Zeit verwenden.
1. Suchen Sie nach Code-Optimierungen oder operativen Optimierungen:
1. Code-Optimierungen: Achten Sie auf die Optimierung von Abfragen mit Masseneinfügungen/Aktualisierungen, die Minimierung der Indexnutzung oder die Drosselung von Code.
1. Operative Optimierungen: Abladung ressourcenintensiver Datenänderungen zur Verringerung der Traffic-Zeiten.
1. Zusätzliche Optimierungen: Stellen Sie sicher, dass Sie die neueste Version von ECE-Tools verwenden. Anweisungen hierzu finden Sie unter [Cloud für Adobe Commerce > ECE-Tools-Version aktualisieren](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

* Informationen zu anderen häufigen MariaDB-Problemen finden Sie unter [Häufigste Datenbankprobleme für Adobe Commerce in Cloud-Infrastrukturen](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html).
* Informationen zu Best Practices für Datenbanken finden Sie unter [Best Practices für Datenbanken für Adobe Commerce in Cloud-Infrastrukturen](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html).
