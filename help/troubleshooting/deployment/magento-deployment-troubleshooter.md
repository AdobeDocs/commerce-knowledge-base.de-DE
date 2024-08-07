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

+++**Ist Adobe Commerce auf dem Cloud-Infrastrukturdienst betriebsbereit?**

Stuck Deployment - Ist Adobe Commerce auf dem Cloud-Infrastrukturdienst verfügbar? Überprüfen Sie [Adobe Commerce Cloud](https://status.adobe.com/products/3350/).

a. YES - Fahren Sie mit [Schritt 2](#step-2) fort.\
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

Informationen zu einer vorhandenen Bereitstellungsaktivität finden Sie unter [Überprüfen des Bereitstellungsprotokolls, wenn in der Cloud-Benutzeroberfläche der Fehler &quot;Log Snipped&quot;(Log Snipped) aufgetreten ist](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error.html)
für Details) können Sie diesen Befehl ausführen, um ein ausführliches Protokoll zu dieser Aktivität zu erhalten:

```bash
magento-cloud activity:log <activity-id> [OPTIONAL: <-p project-id or project-url>]
```

a. YES - Fehlerbehebung bei der anderen Implementierung, die die Implementierung blockiert, in der vorhandenen Umgebung. Fahren Sie mit [Schritt 3](#step-3) fort.

b. NO - Fehlerbehebung in der aktuellen Umgebung. Fahren Sie mit [Schritt 3](#step-3) fort.

+++


## Schritt 3: SSH auf allen Knoten überprüfen {#step-3}

+++**SSH für alle Knoten erfolgreich?**

a. YES - Fahren Sie mit [Schritt 4](#step-4) fort.\
b. NO - [Senden Sie ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Schritt 4: Überprüfen aller ausgeführten Dienste {#step-4}

+++**Alle Dienste werden ausgeführt?**

a. YES - Fahren Sie mit [Schritt 5](#step-5) fort.\
b. NO - [Senden Sie ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Schritt 5: Überprüfen der Ausführung von Bitbuckets {#step-5}

+++**Verwenden von Bitbucket?**

a. YES - Überprüfen Sie [status.bitbucket.com](https://bitbucket.status.atlassian.com/).\
b. NO - Überprüfen Sie die Fehler im Bereitstellungsprotokoll in den [Protokolle zum Erstellen und Bereitstellen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html). Fahren Sie mit [Schritt 6](#step-6) fort.

+++

## Schritt 6: Überprüfen der Fehlercodes {#step-6}

+++**Fehler-Code gemeldet?**

a. YES - Fahren Sie mit [Schritt 7](#step-7) fort.\
b. NO - Fahren Sie mit [Schritt 8](#step-8) fort.

+++

## Schritt 7 - 403 Verbotener Fehler {#step-7}

+++**403 Verboten?**

a. YES - Fahren Sie mit [Schritt 16](#step-16) fort.
b. NO - Fahren Sie mit [Schritt 9](#step-9) fort.

+++

## Schritt 8: Überprüfen der ausgeführten Cron-Aufträge {#step-8}

+++**Laufen derzeit Cron-Aufträge?** Melden Sie sich bei ssh am Zweig an und führen Sie `ps aufxx |grep cron` aus.

a. YES - Melden Sie sich über ssh im betroffenen Zweig an (z. B. primär). Cron-Jobs töten und entsperren. Dadurch werden Cron-Aufträge beendet und der Status zurückgesetzt. Führen Sie `php vendor/bin/ece-tools cron:kill` und dann `php vendor/bin/ece-tools cron:unlock` aus. Wenn Sie gerade dabei waren, eine Umgebung in einer anderen zusammenzuführen, überprüfen Sie beide Umgebungen auf die Ausführung von Crons.\
b. NO - Fahren Sie mit [Schritt 17](#step-17) fort.

+++

## Schritt 9: Auf Remote-Cluster-Fehler bereitstellbare Anwendung {#step-9}

+++**Anwendung kann nicht in den Remote-Cluster-Fehler hochgeladen werden?**

a. YES - Fahren Sie mit [Schritt 10](#step-10) fort.\
b. NO - Fahren Sie mit [Schritt 11](#step-11) fort.

+++

## Schritt 10: Überprüfen des ausreichenden Speichers {#step-10}

+++**Verfügbarer Speicher OK?**

a. YES - Fahren Sie mit [Schritt 11](#step-11) fort.\
b. NO - Überprüfen Sie [Speicherplatz verwalten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html).

+++

## Schritt 11: Überprüfen des Festplattenspeichers {#step-11}

+++**_file konnte nicht geschrieben werden Warning _?**

a. YES - Bitte [erhöhen Sie den Festplattenwert in .magento.app.yaml](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#application-disk-space) und stellen Sie ihn erneut bereit. Wenn dies nicht funktioniert, senden [ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Fahren Sie mit [Schritt 12](#step-12) fort.

+++

## Schritt 12: Fehler bei der Neuimplementierung der Umgebung fehlgeschlagen {#step-12}

+++**Fehler bei der Neubereitstellung der Umgebung fehlgeschlagen?**

a. YES - Fahren Sie mit [Schritt 13](#step-13) fort.\
b. NO - Fahren Sie mit [Schritt 8](#step-8) fort.

+++

## Schritt 13: Auf Elasticsearch-Upgrade überprüfen schlägt fehl {#step-13}

+++**Elasticsearch, das aktualisiert oder bereitgestellt wird?**

a. JA - Elasticsearch ist fehlgeschlagen. Siehe [Elasticsearch-Softwarekompatibilität](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html). Wenn das Elasticsearch-Upgrade weiterhin nicht funktioniert, senden [ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). **Hinweis**: Beachten Sie bei Adobe Commerce in der Cloud-Infrastruktur, dass Service-Upgrades nicht in die Produktionsumgebung übertragen werden können, ohne dass unser Infrastrukturteam 48 Geschäftszeiten benachrichtigt. Dies ist erforderlich, da wir sicherstellen müssen, dass wir über einen Infrastruktur-Support-Mitarbeiter verfügen, der Ihre Konfiguration innerhalb des gewünschten Zeitraums mit minimalen Ausfallzeiten in Ihrer Produktionsumgebung aktualisiert. 48 Stunden vor dem Zeitpunkt, zu dem Ihre Änderungen in der Produktion sein müssen, senden [ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), in dem Sie Ihre erforderliche Service-Aktualisierung und den Zeitpunkt angeben, zu dem der Upgrade-Prozess beginnen soll.\
b. NO - Fahren Sie mit [Schritt 14](#step-14) fort.

+++

## Schritt 14: Überprüfen der Platzierungsgrenzen {#step-14}

+++**Dateisystem außerhalb von Knoten oder Leerzeichen?**

a. YES - Siehe [Verwalten des Festplattenspeichers](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#application-disk-space).\
b. NO - Fahren Sie mit [Schritt 15](#step-15) fort.

+++

## Schritt 15: Fehler bei der Elasticsearch-Version {#step-15}

+++**Fehler bei Elasticsearch-Versionen?**

a. YES - Fahren Sie mit [Schritt 16](#step-16) fort.\
b. NO - Fahren Sie mit [Schritt 21](#step-21) fort.

+++

## Schritt 16: Überprüfen der Komponentenkonfiguration {#step-16}

+++**Composer-Konfiguration korrekt?**

a. YES - Fahren Sie mit [Schritt 10](#step-10) fort.\
b. NO - Überprüfen Sie die Webseite [Composer-Fehlerbehebung](https://getcomposer.org/doc/articles/troubleshooting.md).

+++

## Schritt 17: Auf langwierige Prozesse überprüfen {#step-17}

+++**Lange laufende Prozesse?**

a. YES - Identifizieren Sie langwierige Prozesse und beenden Sie dann Prozesse:
1. Führen Sie den folgenden Befehl im Terminal aus: `ps aufx`.
1. Suchen Sie die PID des langwierigen Prozesses.
1. Beenden Sie den Prozess mit `kill -9 <PID>`.

Implementierungen auf erneutes Auftreten überwachen

b. NO - Fahren Sie mit [Schritt 18](#step-18) fort.

+++

## Schritt 18: Auf einen Post-Hook-Fehler überprüfen {#step-18}

+++**Post-Hook-Fehler/Aufhängen?**

a. YES - Datenbank: [Freier Speicherplatz](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#allocate-disk-space), Beschädigung, unvollständige/beschädigte Tabellen.\
b. NO - Fahren Sie mit [Schritt 19](#step-19) fort.

+++

## Schritt 19: Überprüfen, ob Erweiterungen von Drittanbietern die Bereitstellung blockieren {#step-19}

+++**Verwenden von Drittanbietererweiterungen?**

a. YES - Versuchen Sie, [die Drittanbietererweiterungen zu deaktivieren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/extensions.html) und die Bereitstellung auszuführen (um zu sehen, ob sie die Ursache des Problems sind), insbesondere wenn in Fehlern Erweiterungsnamen vorhanden sind.\
b. NO - Fahren Sie mit [Schritt 20](#step-20) fort.

+++

## Schritt 20: Auf langsame Abfragen überprüfen {#step-20}

+++**Lange laufende Abfragen?**

[Überprüfen Sie das langsame Abfrageprotokoll und MySQL zeigt processlist](/help/troubleshooting/database/checking-slow-queries-and-processes-mysql.md).

a. YES - Schließen Sie alle langwierigen Abfragen ab. Überprüfen Sie die Syntax für MySQL-Fehler.](https://dev.mysql.com/doc/refman/8.0/en/kill.html)[\
b. NO - [Senden Sie ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Schritt 21: Herunterladen der Elasticsearch-Version {#step-21}

+++**Herunterstufen von Elasticsearch-Versionen?**

a. JA - Kann nicht durch Konfiguration durchgeführt werden. [Senden Sie ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - [Senden Sie ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Zurück zu Schritt 1](#step-1)
