---
title: "Verwaltete Warnhinweise zu Adobe Commerce: MariaDB-Warnhinweise"
description: Dieser Artikel enthält Schritte zur Fehlerbehebung, wenn Sie MariaDB-Warnhinweise für Adobe Commerce in New Relic erhalten. Die MariaDB-Warnhinweise überwachen eine hohe Abfragelast sowie übermäßige DML-Abfragen (Data Manipulation Language). Beide können zu einem eingeschränkten Benutzererlebnis oder sogar zu Ausfallzeiten führen. Sie können vier Arten von Warnungen erhalten:'
exl-id: 707e20e0-faba-4bcd-884c-b54568787442
feature: Cache, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# Verwaltete Warnhinweise zu Adobe Commerce: MariaDB-Warnhinweise

Dieser Artikel enthält Schritte zur Fehlerbehebung, wenn Sie MariaDB-Warnhinweise für Adobe Commerce in New Relic erhalten. Die MariaDB-Warnhinweise überwachen eine hohe Abfragelast sowie übermäßige DML-Abfragen (Data Manipulation Language). Beide können zu einem eingeschränkten Benutzererlebnis oder sogar zu Ausfallzeiten führen. Sie können vier Arten von Warnungen erhalten:

* Warnung bei DML-Abfragen
* DML-Abfragen kritisch

## **Betroffene Produkte und Versionen**

Adobe Commerce on Cloud Infrastructure Pro-Planarchitektur

## Problem

Sie erhalten einen Warnhinweis, der in New Relic verwaltet wird, wenn Sie bis zu [Warnhinweise für Adobe Commerce verwalten](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) angemeldet haben und mindestens eine der Warnschwellen überschritten wurde. Diese Warnhinweise wurden von Adobe entwickelt, um Kunden mithilfe von Einblicken aus dem Support und Engineering einen Standardsatz zu liefern.

**Do!**

* Beenden Sie alle geplanten Implementierungen, bis dieser Warnhinweis gelöscht ist.
* Setzen Sie Ihre Site sofort in den Wartungsmodus, wenn Ihre Site vollständig oder gar nicht reagiert. Anweisungen finden Sie unter [Installationshandbuch > Wartungsmodus aktivieren oder deaktivieren](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) in unserer Entwicklerdokumentation. Stellen Sie sicher, dass Sie Ihre IP-Adresse zur Liste der ausgenommenen IP-Adressen hinzufügen, um sicherzustellen, dass Sie weiterhin auf Ihre Website zugreifen können, um die Fehlerbehebung durchzuführen. Anweisungen hierzu finden Sie unter [Verwalten der Liste der ausgenommenen IP-Adressen](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt).
* Beenden Sie Skripte wie Importe, die die Ursache des Warnhinweises sein können, wenn die Site-Leistung beeinträchtigt wird.

**Nicht!**

* Führen Sie Indexer oder zusätzliche Kronen aus, die zusätzliche Belastungen für MariaDB verursachen können.
* Führen Sie alle wichtigen Verwaltungsaufgaben aus (z. B. Commerce-Administrator, Datenimport/-export).
* Löschen Sie den Cache.

## Lösung

**DML-Abfragen (Abfragen, die die Datenbank mit UPDATE, INSERT und DELETE ändern)**

Wenn Sie einen Warnhinweis zu DML-Abfragen erhalten, starten Sie in Schritt 1. Wenn Sie einen Warnhinweis zu DML-Abfragen erhalten, beginnen Sie in Schritt 2.

1. Überprüfen Sie, ob ein Adobe Commerce-Support-Ticket vorhanden ist. Anweisungen hierzu finden Sie in unserer Wissensdatenbank [Tracking Ihrer Support-Tickets](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets). Der Support hat möglicherweise einen New Relic-Schwellenwert-Warnhinweis erhalten, ein Ticket erstellt und mit der Bearbeitung des Problems begonnen. Wenn kein Ticket existiert, erstellen Sie eines. Das Ticket sollte die folgenden Informationen enthalten:
1. Kontaktgrund: Wählen Sie &quot;New Relic MariaDB alert received&quot;.
1. Beschreibung der Warnung.
1. [New Relic-Vorfall-Link](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Dies ist in Ihren [verwalteten Warnhinweisen für Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) enthalten.
1. Um die Ursache des Problems zu ermitteln, versuchen Sie, die DML-Abfragen zu identifizieren:
1. Überprüfen Sie Ihre Datenbankvorgänge, indem Sie die Schritte auf der Seite New Relic [APM UI Pages > Monitoring > Datenbanken](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time) durchführen.
1. Sortieren Sie nach CALL COUNT und dann OPERATION. Überprüfen Sie die Vorgänge INSERT, DELETE und UPDATE .
1. Suchen Sie nach hoher AVG.
1. Klicken Sie durch, um Datenbankoperationsaufrufer zu finden. Dadurch werden Transaktionen anhand dieser Abfrage nach Zeit identifiziert.
1. Suchen Sie nach Code-Optimierungen oder betrieblichen Optimierungen:
1. Codeoptimierungen: Optimieren Sie Abfragen mit Masseneinfügungen/-aktualisierungen, minimieren Sie die Indexverwendung oder den Einschränkungscode.
1. Betriebsoptimierungen: Laden Sie ressourcenintensive Datenänderungen zur Verringerung der Traffic-Zeit ab.
1. Zusätzliche Optimierungen: Stellen Sie sicher, dass Sie die neueste Version der ECE-Tools verwenden. Anweisungen hierzu finden Sie in unserer Entwicklerdokumentation unter [Cloud für Adobe Commerce > Aktualisierung der ece-tools-Version](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package) .

## Verwandte Informationen

* Weitere häufige MariaDB-Probleme finden Sie unter [Häufigste Datenbankprobleme für Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html).
* Informationen zu Best Practices für Datenbanken finden Sie unter [Best Practices für die Datenbank für Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html).
