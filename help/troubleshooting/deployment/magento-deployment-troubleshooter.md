---
title: Fehlerbehebung bei der Adobe Commerce-Bereitstellung
description: Festsitzende Bereitstellungen und fehlgeschlagene Bereitstellungen auf Adobe Commerce können mit dem Tool zur Bereitstellungs-Fehlerbehebung behoben werden. Klicken Sie auf die einzelnen Fragen, um die Antwort in jedem Schritt der Fehlerbehebung anzuzeigen.
exl-id: 5141e079-be61-44c2-8bff-c4b13cb7e07c
feature: Build, Deploy, Support
role: Developer
source-git-commit: aedf869e96ce6bcbf538805dd6d14d31db8c2e02
workflow-type: tm+mt
source-wordcount: '958'
ht-degree: 0%

---

# Fehlerbehebung bei der Adobe Commerce-Bereitstellung

Festsitzende Bereitstellungen und fehlgeschlagene Bereitstellungen auf Adobe Commerce können mit dem Tool zur Bereitstellungs-Fehlerbehebung behoben werden. Klicken Sie auf die einzelnen Fragen, um die Antwort in jedem Schritt der Fehlerbehebung anzuzeigen.

## Schritt 1: Überprüfen, ob der Dienst ausgeführt wird {#step-1}

+++**Ist Adobe Commerce auf Cloud-Infrastruktur-Service aktiv?**

Stack Deployment - Ist Adobe Commerce auf Cloud-Infrastruktur-Service aktiv? [Adobe Commerce Cloud ](https://status.adobe.com/products/3350/).

a. JA - Mit [Schritt 2](#step-2) fortfahren.\
b. NEIN - Wartung oder globale Ausfälle. Prüfen Sie auf geschätzte Dauer und Aktualisierungen.

+++

## Schritt 2: Überprüfen Sie Bereitstellungen in anderen Umgebungen. {#step-2}

+++**Gibt es Bereitstellungen in anderen Umgebungen, die die Bereitstellung in der vorhandenen Umgebung blockieren?**

Um eine Liste der laufenden Aktivitäten zu erhalten, führen Sie den folgenden Befehl mithilfe der Magento-Cloud-CLI aus (wenn Sie nur zu einem Cloud-Projekt hinzugefügt wurden). **Hinweis**: Vergewissern Sie sich, dass Sie die neueste Version von magento-cloud CLI verwenden. Anweisungen hierzu finden Sie unter [Aktualisieren der CLI](/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli/cloud-cli-overview) im Handbuch Commerce on Cloud Infrastructure .

```bash
magento-cloud --state=in_progress
```

Um eine Liste der laufenden Aktivitäten zu erhalten, führen Sie den folgenden Befehl mithilfe der Magento-Cloud-CLI aus (wenn Sie mehreren Projekten hinzugefügt wurden):

```bash
magento-cloud -p <project-id or project-url> --state=in_progress
```

Informationen zu einer vorhandenen Bereitstellungsaktivität finden Sie unter [Überprüfen des Bereitstellungsprotokolls, wenn in der Cloud-Benutzeroberfläche der Fehler „Protokoll abgeschnitten“ auftritt](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error.html)
(für Details) Sie können diesen Befehl ausführen, um ein ausführendes Protokoll dieser Aktivität abzurufen:

```bash
magento-cloud activity:log <activity-id> [OPTIONAL: <-p project-id or project-url>]
```

a. JA - Fehlerbehebung bei Problemen mit der anderen Umgebung, die die Bereitstellung in der vorhandenen Umgebung blockiert. Fahren Sie mit [Schritt 3](#step-3) fort.

b. NEIN - Fehlerbehebung in der aktuellen Umgebung. Fahren Sie mit [Schritt 3](#step-3) fort.

+++


## Schritt 3: Überprüfen von SSH auf allen Knoten {#step-3}

+++**SSH erfolgreich auf allen Knoten?**

a. JA - Mit [Schritt 4](#step-4) fortfahren.\
b. NEIN - [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Schritt 4: Überprüfen aller laufenden Dienste {#step-4}

+++**Alle Dienste werden ausgeführt?**

a. JA - Mit [Schritt 5](#step-5) fortfahren.\
b. NEIN - [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Schritt 5: Bitbucket-Ausführung überprüfen {#step-5}

+++**Mit Bitbucket?**

a. JA - Überprüfen Sie [status.bitbucket.com](https://bitbucket.status.atlassian.com/).\
b. NEIN - Überprüfen Sie die Bereitstellungsprotokollfehler in den [Build- und Bereitstellungsprotokollen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html). Fahren Sie mit [Schritt 6](#step-6) fort.

+++

## Schritt 6: Fehlercodes überprüfen {#step-6}

+++**Fehlercode gemeldet?**

a. JA - Mit [Schritt 7](#step-7) fortfahren.\
b. NEIN - Fahren Sie mit [Schritt 8](#step-8) fort.

+++

## Schritt 7: 403 Fehler „Forbidden“ {#step-7}

+++**403 verboten?**

a. JA - Mit [Schritt 16](#step-16) fortfahren.
b. NEIN - Fahren Sie mit [Schritt 9](#step-9) fort.

+++

## Schritt 8: Überprüfen der laufenden Cron-Aufträge {#step-8}

+++**Werden Cron-Aufträge derzeit ausgeführt?** Melden Sie sich mit ssh in der Verzweigung an und führen Sie `ps aufxx |grep cron` aus.

a. JA - Melden Sie sich über ssh bei der betroffenen Verzweigung an (z. B. primary). Töte und erschließe Cron-Aufträge. Dadurch werden Cron-Aufträge beendet und der Status zurückgesetzt. Führen Sie `php vendor/bin/ece-tools cron:kill` und dann `php vendor/bin/ece-tools cron:unlock` aus. Wenn Sie dabei waren, eine Umgebung in eine andere zusammenzuführen, überprüfen Sie beide Umgebungen auf aktive Crons.\
b. NEIN - Mit [Schritt 17](#step-17) fortfahren.

+++

## Schritt 9: Fehler „Anwendung für Remote-Cluster bereitstellbar“ {#step-9}

+++**Die Anwendung kann nicht auf den Remote-Cluster-Fehler hochgeladen werden?**

a. JA - Mit [Schritt 10](#step-10) fortfahren.\
b. NEIN - Mit [Schritt 11](#step-11) fortfahren.

+++

## Schritt 10: Prüfen Sie, ob ausreichend Speicherplatz vorhanden ist {#step-10}

+++**Verfügbarer Speicher okay?**

a. JA - Fahren Sie mit [Schritt 11](#step-11) fort.\
b. NEIN - Überprüfen Sie [Speicherplatz verwalten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html).

+++

## Schritt 11: Überprüfen Sie den Festplattenspeicher. {#step-11}

+++**_Datei konnte nicht geschrieben werden. Warnung _?**

a. JA - Bitte [den Datenträgerwert in &quot;.magento.app.yaml“ erhöhen ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#application-disk-space) erneut bereitstellen. Wenn dies nicht funktioniert, [ein Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NEIN - Fahren Sie mit [Schritt 12](#step-12) fort.

+++

## Schritt 12: Fehler „Umgebung-Neubereitstellung fehlgeschlagen“ {#step-12}

+++**Fehler bei fehlgeschlagener Umgebungsbereitstellung?**

a. JA - Fahren Sie mit [Schritt 13](#step-13) fort.\
b. NEIN - Fahren Sie mit [Schritt 8](#step-8) fort.

+++

## Schritt 13: Überprüfung auf fehlgeschlagene Elasticsearch-Aktualisierung {#step-13}

+++**Elasticsearch wird aktualisiert oder bereitgestellt?**

a. JA - Fehlgeschlagene Upgrade-Schritte für Elasticsearch. Siehe [Kompatibilität der Elasticsearch-Software](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html). Wenn das Elasticsearch-Upgrade immer noch nicht funktioniert, [ Sie ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). **Hinweis**: Bei Adobe Commerce auf Cloud-Infrastrukturen ist zu beachten, dass Service-Upgrades nicht ohne Vorankündigung innerhalb von 48 Geschäftsstunden an unser Infrastruktur-Team in die Produktionsumgebung übertragen werden können. Dies ist erforderlich, da wir sicherstellen müssen, dass wir einen Support-Techniker für die Infrastruktur zur Verfügung haben, der Ihre Konfiguration innerhalb des gewünschten Zeitrahmens mit minimalen Ausfallzeiten in Ihrer Produktionsumgebung aktualisiert. 48 Stunden vor dem Zeitpunkt, zu dem Ihre Änderungen in der Produktion sein müssen, [ Sie ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), in dem Sie die erforderliche Service-Aktualisierung detailliert beschreiben und den Zeitpunkt angeben, zu dem der Upgrade-Prozess beginnen soll.\
b. NEIN - Mit [Schritt 14](#step-14) fortfahren.

+++

## Schritt 14: Überprüfung der Speicherplatzbeschränkungen {#step-14}

+++**Nicht genügend Inodes oder Speicherplatz im Dateisystem**

a. JA - Siehe [Speicherplatz verwalten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#application-disk-space).\
b. NEIN - Mit [Schritt 15](#step-15) fortfahren.

+++

## Schritt 15: Fehler bei Elasticsearch-Version {#step-15}

+++**Fehler bei Elasticseach-Versionen?**

a. JA - Mit [Schritt 16](#step-16) fortfahren.\
b. NEIN - Mit [Schritt 21](#step-21) fortfahren.

+++

## Schritt 16: Überprüfen der Composer-Konfiguration {#step-16}

+++**Composer-Konfiguration korrekt?**

a. JA - Mit [Schritt 10](#step-10) fortfahren.\
b. NEIN - Überprüfen Sie [Composer-Fehlerbehebungs-Webseite](https://getcomposer.org/doc/articles/troubleshooting.md).

+++

## Schritt 17: Prüfen auf lange laufende Prozesse {#step-17}

+++**Lang laufende Prozesse?**

a. JA - Ermitteln Sie Prozesse mit langer Laufzeit und beenden Sie sie dann:
1. Führen Sie den folgenden Befehl am Terminal aus: `ps aufx`.
1. Suchen Sie die PID des langwierigen Prozesses.
1. Beenden Sie den Prozess mithilfe von `kill -9 <PID>`.

Überwachen von Bereitstellungen auf Wiederholungen.

b. NEIN - Fahren Sie mit [Schritt 18](#step-18) fort.

+++

## Schritt 18 - Auf Fehler beim Pfosten-Haken prüfen {#step-18}

+++**Post Hook Failure/Hang?**

a. JA - Datenbank: [Freier Speicherplatz](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#allocate-disk-space), Beschädigung, unvollständige/beschädigte Tabellen.\
b. NEIN - Fahren Sie mit [Schritt 19](#step-19) fort.

+++

## Schritt 19: Überprüfen, ob Erweiterungen von Drittanbietern die Bereitstellung blockieren {#step-19}

+++**Verwendung von Erweiterungen von Drittanbietern?**

A. JA - Versuchen Sie [Drittanbietererweiterungen deaktivieren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/extensions.html) und führen Sie die Bereitstellung aus (um zu sehen, ob sie die Ursache des Problems sind), insbesondere wenn in Fehlern Erweiterungsnamen enthalten sind.\
b. NEIN - Mit [Schritt 20](#step-20) fortfahren.

+++

## Schritt 20: Prüfen auf langsame Abfragen {#step-20}

+++**Lang laufende Abfragen?**

[Überprüfen Sie das langsame Abfrageprotokoll und die Prozessliste in MySQL anzeigen](/help/troubleshooting/database/checking-slow-queries-and-processes-mysql.md).

a. JA - Alle lang laufenden Abfragen beenden. Review [MySQL Kill Syntax.](https://dev.mysql.com/doc/refman/8.0/en/kill.html)\
b. NEIN - [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Schritt 21 - Elasticsearch-Version herunterstufen {#step-21}

+++**Herabstufen von Elasticsearch-Versionen?**

a. JA - Kann nicht über die Konfiguration ausgeführt werden. [Senden eines Support-Tickets](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NEIN - [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Zurück zu Schritt 1](#step-1)
