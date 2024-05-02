---
title: Fehlerbehebung bei der erweiterten Berichterstellung für Adobe Commerce
description: Probleme mit erweiterten Berichten in Adobe Commerce können mit diesem Tool zur Fehlerbehebung behoben werden. Dazu gehört auch die erweiterte Berichterstellung ohne Daten und 404-Fehler. Klicken Sie auf jede Frage, um die Antwort in jedem Schritt der Problembehebung anzuzeigen.
exl-id: 7ef9870c-b6b6-4144-a5a7-81aa20a1606c
feature: Cache, Support
role: Developer
source-git-commit: 84b4ca4c4144381f0b404d2eae6684e7b21755df
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 0%

---

# Fehlerbehebung bei der erweiterten Berichterstellung für Adobe Commerce

Probleme mit erweiterten Berichten in Adobe Commerce können mit diesem Tool zur Fehlerbehebung behoben werden. Dazu gehört auch die erweiterte Berichterstellung ohne Daten und 404-Fehler. Klicken Sie auf jede Frage, um die Antwort in jedem Schritt der Problembehebung anzuzeigen.

## Schritt 1: Bestätigen, dass die Site die erweiterten Berichterstellungsanforderungen erfüllt {#step-1}

+++**Erfüllt Ihre Website die erweiterten Reporting-Anforderungen?**

Bei Verwendung der erweiterten Berichterstellung weist die Seite 404 Fehler auf. Erfüllt Ihre Website Ihre Anforderungen? [Erweiterte Berichtsanforderungen](https://docs.magento.com/user-guide/reports/advanced-reporting.html#requirements)?

a. JA - fahren Sie mit [Schritt 2](#step-2).\
b. NO - Führen Sie die erweiterten Berichterstellungsanforderungen für Ihre Site aus, indem Sie die Schritte unter [Erweiterte Berichtsanforderungen](https://docs.magento.com/user-guide/reports/advanced-reporting.html#requirements). Fahren Sie dann mit [Schritt 2](#step-2).

+++

## 2. Schritt - Gibt es Bestellungen in mehreren Basiswährungen? {#step-2}

+++**Werden mehrere Basiswährungen verwendet?**

Werden mehrere Basiswährungen verwendet (in Bestellungen und Konfiguration)? Führen Sie diesen SQL-Befehl aus, um die aktuelle Konfiguration abzurufen: `SELECT value FROM core_config_data WHERE path = 'currency/options/base';` .

a. YES - Wenn mehrere Zeilen von der Abfrage zurückgegeben werden, können Sie die erweiterte Berichterstellung nicht verwenden, da wir nur eine Währung unterstützen.\
b. NO - Die Ausgabe zeigt nur eine Währung an. Beispiel: `USD`. Wurden schon mehrere Basiswährungen verwendet (in Bestellungen)? Führen Sie diesen SQL-Befehl aus, um Verlaufsbestellungsdaten abzurufen:\
`SELECT DISTINCT base_currency_code FROM sales_order;`.
**HINWEIS: Für diesen Befehl ist eine vollständige Tabellenüberprüfung erforderlich. Bei Tabellen mit einer hohen Datensatzanzahl kann sich dies daher auf die Leistung auswirken, während die Abfrage ausgeführt wird.** , um historische Auftragsdaten zu erhalten.
Wenn mehrere Basiswährungen jemals verwendet wurden, können Sie keine erweiterte Berichterstellung verwenden, da wir nur eine Währung unterstützen. Wenn nur eine Währung angezeigt wird, fahren Sie mit [Schritt 3](#step-3).

+++

## Schritt 3: Überprüfen, ob die verwendete geteilte Datenbank verwendet wird {#step-3}

+++**Verwenden Sie eine Aufspaltungs-Datenbanklösung?**

Verwenden Sie [Split-Datenbanklösung](https://devdocs.magento.com/guides/v2.3/config-guide/multi-master/multi-master.html)?

a. JA - Den Patch verwenden **MDVA-26831** in [Fehler &quot;Erweiterte Berichterstellung 404&quot;in der geteilten Datenbanklösung](/help/troubleshooting/known-issues-patches-attached/advanced-reporting-404-error-on-split-database-solution.md) und leeren Sie den Cache. Warten Sie 24 Stunden, bis der Auftrag erneut ausgeführt wird, und versuchen Sie es erneut.\
b. NO - Fahren Sie mit [Schritt 4](#step-4).

+++

## Schritt 4: Bestätigen der Aktivierung der erweiterten Berichterstellung {#step-4}

+++**Ist die erweiterte Berichterstellung aktiviert?**

Überprüfen **Admin** > **Stores** > **Einstellungen** > **Konfiguration** > **Allgemein** > **Erweitert**. Detaillierte Schritte finden Sie unter [Fortschrittliche Berichterstellung: Erweiterte Berichterstellung aktivieren](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting).

a. JA - fahren Sie mit [Schritt 5](#step-5).\
b. NO - [Erweiterte Berichterstellung aktivieren](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting) und speichern Sie und warten Sie 24 Stunden, bis Adobe Commerce und die erweiterte Berichterstellung synchronisiert sind. Überprüfen Sie, ob Ihre Daten jetzt geladen werden. Wenn es das Problem gelöst hat. Wenn er nicht fortfährt, fahren Sie mit [Schritt 5](#step-5).

+++

## Schritt 5: Auf Token suchen {#step-5}

+++**Gibt es ein Token?**

Stellen Sie sicher, dass ein Token vorhanden ist, indem Sie die folgende Abfrage ausführen: `SELECT * FROM core_config_data WHERE path LIKE 'analytics/general/token' \G` Gibt es ein Token?

a. JA - fahren Sie mit [Schritt 7](#step-7).\
b. NO - Wenn der Token-Wert NULL ist oder sich kein Datensatz in der Datenbank befindet, fahren Sie mit [Schritt 6](#step-6).

+++

## 6. Schritt - Zeile verwenden {#step-6}

+++**Gibt die Abfrage die Zeile zurück?**

Überprüfen Sie den Zählerwert in der Kennzeichnungstabelle, indem Sie diese Abfrage ausführen: ``SELECT * FROM `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter'\G`` Gibt die Abfrage die Zeile zurück?

a. JA - Gehen Sie wie folgt vor: 1. Führen Sie die folgende Abfrage aus:\
``DELETE from `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter';``\
2\. [Modul &quot;Erweiterte Berichterstellung deaktivieren und aktivieren&quot;](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting) in den Einstellungen und [Erneutes Autorisieren des Tokens](https://docs.magento.com/user-guide/reports/advanced-reporting.html#verify-that-the-integration-is-active).\
3\. Warten Sie 24 Stunden, bis Adobe Commerce und die erweiterte Berichterstellung synchronisiert sind. Wenn Sie weiterhin keine Daten in der erweiterten Berichterstellung sehen können, [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Wenn die Abfrage nichts zurückgibt, gehen Sie wie folgt vor: 1. [Modul &quot;Erweiterte Berichterstellung deaktivieren und aktivieren&quot;](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting) in den Einstellungen und [Erneutes Autorisieren des Tokens](https://docs.magento.com/user-guide/reports/advanced-reporting.html#verify-that-the-integration-is-active).\
2\. Warten Sie 24 Stunden, bis Adobe Commerce und die erweiterte Berichterstellung synchronisiert sind. Wenn Sie weiterhin keine Daten in der erweiterten Berichterstellung sehen können, [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Schritt 7: Auf Datensätze überprüfen in `cron_schedule` table {#step-7}

+++**Gibt es Datensätze in der `cron_schedule` Tabelle?**

Auftrag überprüfen `analytics_collect_data` durch Ausführen dieser Abfrage ausgeführt wurde: `SELECT * FROM cron_schedule WHERE job_code LIKE 'analytics_collect_data' \G`

a. JA - Wenn Datensätze vorhanden sind und die Variable **status** Spalte sagt _miss_ verwenden Sie den Patch in diesem KB-Artikel [Aktualisierung der erweiterten Berichterstellung für die Ausführung auf eigene Cron-Gruppe](/help/troubleshooting/known-issues-patches-attached/update-advanced-reporting-to-run-on-its-own-cron-group.md).\
b. JA - Wenn es Datensätze gibt und die **status** Spalte sagt _success_, fahren Sie fort mit [Schritt 9](#step-9).\
c. JA - Wenn es Datensätze gibt und die **status** Spalte sagt _error_, fahren Sie fort mit [Schritt 8.](#step-8)\
d. NO - Wenn keine Datensätze vorhanden sind, fahren Sie mit [Schritt 8](#step-8).

+++

## Schritt 8: Überprüfen auf Auftrag in `support_report.log` {#step-8}

+++**Wurde der Auftrag angemeldet? `support_report.log`?**

Führen Sie den Befehl aus: `zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz | tail`

a. YES - Wenn die Ausgabe aus der Abfrage beispielsweise einen erfolgreichen Auftrag anzeigt `Cron Job analytics_collect_data is successfully finished` fortfahren [Schritt 9](#step-9).\
b. NO - Wenn keine Datensätze im Protokoll enthalten sind, [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
c. JA - Wenn Datensätze vorhanden sind, aber ein Fehler auftritt, fahren Sie mit [Schritt 10](#step-10).

+++

## Schritt 9: Suchen nach `data.tgz` file {#step-9}

+++**Gibt die Datei an `data.tgz` existieren im System und gibt es Datensätze in den Zugriffsprotokollen?**

Überprüfen der Datei `data.tgz` vorhanden, Befehl ausführen:

```
ls -ltr pub/media/analytics/<there should be a directory with hash name>/
```

Um zu überprüfen, ob in access.logs Einträge vorhanden sind, führen Sie den Befehl aus:

```
zgrep -i analytics /var/log/platform/[cluster_id|cluster_id_stg]/access.log* | grep MagentoBI
```

a. JA - Wenn die Datei `data.tgz` vorhanden ist und sich Datensätze in den Zugriffsprotokollen befinden. Wenn Sie jedoch weiterhin einen 404-Fehler haben, müssen Sie [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Fahren Sie mit [Schritt 10](#step-10).

+++

## Schritt 10: Überprüfen der Fehlermeldung {#step-10}

+++**Gibt es eine Fehlermeldung, die vom Cron-Auftrag ausgegeben wird?**

Beispiel: Im `core_config_data` Tabelle, in der der Fehler angezeigt wird *Die Datei &quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd4588a0000850c0&quot;kann nicht gelöscht werden.*. Warnung!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a000850c0?lang=en): Keine solche Datei oder Verzeichnis*

a. YES - Verwenden Sie den Patch ACSD-50165 in [Die Datei kann nicht gelöscht werden. Warning!unlink: Kein solcher Datei- oder Verzeichnisfehler vom Administrator](/help/troubleshooting/miscellaneous/file-cannot-be-deleated-no-file-or-directory.md), warten Sie 24 Stunden, bis der Auftrag erneut ausgeführt wird, und versuchen Sie es dann erneut.\
b. NO - Fahren Sie mit [Schritt 11](#step-11).

+++

## Schritt 11: Überprüfen, ob der Fehler &quot;Seitenaufbau&quot;vorliegt {#step-11}

+++**Gibt es einen Fehler, der vom Seitenaufbau verursacht wurde?**

Beispiel: `report.ERROR: Cron Job analytics_collect_data has an error: substr_count() expects parameter 1 to be string, null given. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":224919552,"emalloc_start":216398384} [] []`

a. JA - Verwenden Sie den Patch MDVA-19391 in [Häufige Cron-Auftragsfehler bei der erweiterten Berichterstellung in Adobe Commerce](/help/troubleshooting/known-issues-patches-attached/advanced-reporting-cron-job-errors-magento-commerce.md), warten Sie 24 Stunden, bis der Auftrag erneut ausgeführt wird, und versuchen Sie es erneut.\
b. NO - [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Zurück zu Schritt 1](#step-1)
