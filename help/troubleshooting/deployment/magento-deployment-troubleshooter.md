---
title: Fehlerbehebung bei der Adobe Commerce-Bereitstellung
description: Stuckende Implementierungen und fehlgeschlagene Bereitstellungen in Adobe Commerce können mit dem Tool für die Problembehebung bei der Bereitstellung gelöst werden. Klicken Sie auf jede Frage, um die Antwort in jedem Schritt der Problembehebung anzuzeigen.
exl-id: 5141e079-be61-44c2-8bff-c4b13cb7e07c
feature: Build, Deploy, Support
role: Developer
source-git-commit: 6177863da268f43cc30119cef6f718a04c46b3e6
workflow-type: tm+mt
source-wordcount: '933'
ht-degree: 0%

---

# Fehlerbehebung bei der Adobe Commerce-Bereitstellung

Stuckende Implementierungen und fehlgeschlagene Bereitstellungen in Adobe Commerce können mit dem Tool für die Problembehebung bei der Bereitstellung gelöst werden. Klicken Sie auf jede Frage, um die Antwort in jedem Schritt der Problembehebung anzuzeigen.

## Schritt 1: Überprüfen der Ausführung des Dienstes {#step-1}

+++**Ist Adobe Commerce im Cloud-Infrastrukturdienst verfügbar?**

Stuck Deployment - Ist Adobe Commerce auf dem Cloud-Infrastrukturdienst verfügbar? Überprüfen [Adobe Commerce Cloud](https://status.adobe.com/products/3350/).

a. JA - fahren Sie mit [Schritt 2](#step-2).\
b. NO - Wartungsarbeiten oder globale Ausfälle. Überprüfen Sie die geschätzte Dauer und Updates.

+++

## Schritt 2: Überprüfen von Bereitstellungen in anderen Umgebungen {#step-2}

+++**Gibt es Bereitstellungen in anderen Umgebungen, die die Bereitstellung in der vorhandenen Umgebung blockieren?**

Um eine Liste der laufenden Aktivitäten zu erhalten, führen Sie den folgenden Befehl mit der magento-cloud-CLI aus (wenn Sie nur zu einem Cloud-Projekt hinzugefügt wurden):

```bash
magento-cloud --state=in_progress
```

Um eine Liste der laufenden Aktivitäten zu erhalten, führen Sie den folgenden Befehl mit der magento-cloud-CLI aus (wenn Sie mehreren Projekten hinzugefügt wurden):

```bash
magento-cloud -p <project-id or project-url> --state=in_progress
```

Informationen zu einer vorhandenen Implementierungsaktivität finden Sie unter [Überprüfen des Bereitstellungsprotokolls, wenn die Cloud-Benutzeroberfläche den Fehler &quot;Log Snipped&quot; aufweist](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error.html)
für Details) können Sie diesen Befehl ausführen, um ein ausführliches Protokoll zu dieser Aktivität zu erhalten:

```bash
magento-cloud activity:log <activity-id> [OPTIONAL: <-p project-id or project-url>]
```

a. YES - Fehlerbehebung bei der anderen Implementierung, die die Implementierung blockiert, in der vorhandenen Umgebung. Fahren Sie mit [Schritt 3](#step-3).

b. NO - Fehlerbehebung in der aktuellen Umgebung. Fahren Sie mit [Schritt 3](#step-3).

+++


## Schritt 3: SSH auf allen Knoten überprüfen {#step-3}

+++**SSH für alle Knoten erfolgreich?**

a. JA - fahren Sie mit [Schritt 4](#step-4).\
b. NO - [Support-Ticket senden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Schritt 4: Überprüfen aller ausgeführten Dienste {#step-4}

+++**Alle Dienste laufen?**

a. JA - fahren Sie mit [Schritt 5](#step-5).\
b. NO - [Support-Ticket senden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Schritt 5: Überprüfen der Ausführung von Bitbuckets {#step-5}

+++**Verwenden von Bitbucket?**

a. JA - Prüfung [status.bitbucket.com](https://bitbucket.status.atlassian.com/).\
b. NO - Überprüfen Sie die Fehler im Bereitstellungsprotokoll im [Protokolle erstellen und bereitstellen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html). Fahren Sie mit [Schritt 6](#step-6).

+++

## Schritt 6: Überprüfen der Fehlercodes {#step-6}

+++**Fehler-Code gemeldet?**

a. JA - fahren Sie mit [Schritt 7](#step-7).\
b. NO - Fahren Sie mit [Schritt 8](#step-8).

+++

## Schritt 7 - 403 Verbotener Fehler {#step-7}

+++**403 Verboten?**

a. JA - fahren Sie mit [Schritt 16](#step-16).
b. NO - Fahren Sie mit [Schritt 9](#step-9).

+++

## Schritt 8: Überprüfen der ausgeführten Cron-Aufträge {#step-8}

+++**Laufen derzeit Cron-Aufträge?** Melden Sie sich bei ssh am Zweig an und führen Sie `ps aufxx |grep cron`.

a. YES - Melden Sie sich über ssh im betroffenen Zweig an (z. B. primär). Cron-Jobs töten und entsperren. Dadurch werden Cron-Aufträge beendet und der Status zurückgesetzt. Ausführen `php vendor/bin/ece-tools cron:kill` und dann `php vendor/bin/ece-tools cron:unlock`. Wenn Sie gerade dabei waren, eine Umgebung in einer anderen zusammenzuführen, überprüfen Sie beide Umgebungen auf die Ausführung von Crons.\
b. NO - Fahren Sie mit [Schritt 17](#step-17).

+++

## Schritt 9: Auf Remote-Cluster-Fehler bereitstellbare Anwendung {#step-9}

+++**Kann die Anwendung nicht in den Remote-Cluster-Fehler hochgeladen werden?**

a. JA - fahren Sie mit [Schritt 10](#step-10).\
b. NO - Fahren Sie mit [Schritt 11](#step-11).

+++

## Schritt 10: Überprüfen des ausreichenden Speichers {#step-10}

+++**Verfügbarer Speicher in Ordnung?**

a. JA - Fortfahren mit [Schritt 11](#step-11).\
b. NO - Überprüfung [Verwalten des Festplattenspeichers](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html).

+++

## Schritt 11: Überprüfen des Festplattenspeichers {#step-11}

+++**_-Datei konnte nicht geschrieben werden Warnung _?**

a. JA - Bitte [den Festplattenwert in .magento.app.yaml erhöhen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#application-disk-space) und erneut bereitstellen. Wenn dies nicht funktioniert, [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Fortfahren mit [Schritt 12](#step-12).

+++

## Schritt 12: Fehler bei der Neuimplementierung der Umgebung fehlgeschlagen {#step-12}

+++**Fehler bei der Neubereitstellung der Umgebung?**

a. JA - Fortfahren mit [Schritt 13](#step-13).\
b. NO - Fortfahren mit [Schritt 8](#step-8).

+++

## Schritt 13: Auf Elasticsearch-Upgrade überprüfen schlägt fehl {#step-13}

+++**Elasticsearch wird aktualisiert oder bereitgestellt?**

a. JA - Elasticsearch ist fehlgeschlagen. Siehe Abschnitt [Elasticsearch-Softwarekompatibilität](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html). Wenn das Elasticsearch-Upgrade weiterhin nicht funktioniert, [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). **Hinweis**: Beachten Sie bei Adobe Commerce in der Cloud-Infrastruktur, dass Service-Upgrades nicht in die Produktionsumgebung übertragen werden können, ohne dass unser Infrastrukturteam 48 Geschäftszeiten benachrichtigt. Dies ist erforderlich, da wir sicherstellen müssen, dass wir über einen Infrastruktur-Support-Mitarbeiter verfügen, der Ihre Konfiguration innerhalb des gewünschten Zeitraums mit minimalen Ausfallzeiten in Ihrer Produktionsumgebung aktualisiert. 48 Stunden vor dem Zeitpunkt, zu dem Ihre Änderungen in der Produktion sein müssen, [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) Geben Sie die erforderliche Dienstaktualisierung an und geben Sie den Zeitpunkt an, zu dem die Aktualisierung beginnen soll.\
b. NO - Fahren Sie mit [Schritt 14](#step-14).

+++

## Schritt 14: Überprüfen der Platzierungsgrenzen {#step-14}

+++**Dateisystem außerhalb der Knöpfe oder des Speicherplatzes?**

a. JA - Siehe [Verwalten des Festplattenspeichers](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#application-disk-space).\
b. NO - Fahren Sie mit [Schritt 15](#step-15).

+++

## Schritt 15: Fehler bei der Elasticsearch-Version {#step-15}

+++**Fehler bei Elasticseach-Versionen?**

a. JA - fahren Sie mit [Schritt 16](#step-16).\
b. NO - Fahren Sie mit [Schritt 21](#step-21).

+++

## Schritt 16: Überprüfen der Komponentenkonfiguration {#step-16}

+++**Komponentenkonfiguration korrekt?**

a. JA - fahren Sie mit [Schritt 10](#step-10).\
b. NO - Überprüfung [Website zur Problembehebung in Composer](https://getcomposer.org/doc/articles/troubleshooting.md).

+++

## Schritt 17: Auf langwierige Prozesse überprüfen {#step-17}

+++**Lange laufende Prozesse?**

a. YES - Identifizieren Sie langwierige Prozesse und beenden Sie dann Prozesse:
1. Führen Sie den folgenden Befehl im Terminal aus: `ps aufx`.
1. Suchen Sie die PID des langwierigen Prozesses.
1. Beenden Sie den Prozess mit `kill -9 <PID>`.

Implementierungen auf erneutes Auftreten überwachen

b. NO - Fahren Sie mit [Schritt 18](#step-18).

+++

## Schritt 18: Auf einen Post-Hook-Fehler überprüfen {#step-18}

+++**Post-Hook-Fehler/Aufhängen?**

a. JA - Datenbank: [Freier Speicherplatz](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#allocate-disk-space), Beschädigung, unvollständige/beschädigte Tabellen.\
b. NO - Fahren Sie mit [Schritt 19](#step-19).

+++

## Schritt 19: Überprüfen, ob Erweiterungen von Drittanbietern die Bereitstellung blockieren {#step-19}

+++**Verwenden von Drittanbietererweiterungen?**

a. JA - Versuchen [Deaktivieren der Erweiterungen von Drittanbietern](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/extensions.html) und die Implementierung ausführen (um zu sehen, ob sie die Ursache des Problems sind), insbesondere wenn in Fehlern Erweiterungsnamen enthalten sind.\
b. NO - Fahren Sie mit [Schritt 20](#step-20).

+++

## Schritt 20: Auf langsame Abfragen überprüfen {#step-20}

+++**Lange laufende Abfragen?**

[Überprüfen Sie langsame Abfrage und MySQL zeigt ProcessList](/help/troubleshooting/database/checking-slow-queries-and-processes-mysql.md).

a. YES - Schließen Sie alle langwierigen Abfragen ab. Überprüfen [MySQL-Kill-Syntax.](https://dev.mysql.com/doc/refman/8.0/en/kill.html)\
b. NO - [Support-Ticket senden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Schritt 21: Herunterladen der Elasticsearch-Version {#step-21}

+++**Elasticsearch-Versionen herunterstufen?**

a. JA - Kann nicht durch Konfiguration durchgeführt werden. [Support-Ticket senden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - [Support-Ticket senden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Zurück zu Schritt 1](#step-1)
