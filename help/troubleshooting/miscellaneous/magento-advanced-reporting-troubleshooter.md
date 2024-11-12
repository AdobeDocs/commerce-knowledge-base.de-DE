---
title: Fehlerbehebung bei der erweiterten Berichterstellung für Adobe Commerce
description: Probleme mit erweiterten Berichten in Adobe Commerce können mit diesem Tool zur Fehlerbehebung behoben werden. Dazu gehört auch die erweiterte Berichterstellung ohne Daten und 404-Fehler. Klicken Sie auf jede Frage, um die Antwort in jedem Schritt der Problembehebung anzuzeigen.
exl-id: 7ef9870c-b6b6-4144-a5a7-81aa20a1606c
feature: Cache, Support
role: Developer
source-git-commit: 3b402728be7a80b62f21319d2cf91a92f1ad4a0c
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 0%

---

# Fehlerbehebung bei der erweiterten Berichterstellung für Adobe Commerce

Probleme mit erweiterten Berichten in Adobe Commerce können mit diesem Tool zur Fehlerbehebung behoben werden. Dazu gehört auch die erweiterte Berichterstellung ohne Daten und 404-Fehler. Klicken Sie auf jede Frage, um die Antwort in jedem Schritt der Problembehebung anzuzeigen.

## Schritt 1: Bestätigen, dass die Site die erweiterten Berichterstellungsanforderungen erfüllt {#step-1}

+++**Erfüllt Ihre Website die erweiterten Berichterstellungsanforderungen?**

Bei Verwendung der erweiterten Berichterstellung weist die Seite 404 Fehler auf. Erfüllt Ihre Website die [erweiterten Berichterstellungsanforderungen](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#requirements)?

a. YES - Fahren Sie mit [Schritt 2](#step-2) fort.\
b. NO - Führen Sie die erweiterten Berichterstellungsanforderungen für Ihre Site aus, indem Sie die Schritte unter [Erweiterte Berichterstellungsanforderungen](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#requirements) ausführen. Fahren Sie dann mit [Schritt 2](#step-2) fort.

+++

## 2. Schritt - Gibt es Bestellungen in mehreren Basiswährungen? {#step-2}

+++**Werden mehrere Basiswährungen verwendet?**

Werden mehrere Basiswährungen verwendet (in Bestellungen und Konfiguration)? Führen Sie diesen Befehl [!DNL SQL] aus, um die aktuelle Konfiguration zu erhalten: `SELECT value FROM core_config_data WHERE path = 'currency/options/base';` .

a. YES - Wenn mehrere Zeilen von der Abfrage zurückgegeben werden, können Sie die erweiterte Berichterstellung nicht verwenden, da wir nur eine Währung unterstützen.\
b. NO - Die Ausgabe zeigt nur eine Währung an. Beispiel: `USD`. Wurden schon mehrere Basiswährungen verwendet (in Bestellungen)? Führen Sie diesen Befehl [!DNL SQL] aus, um Verlaufsbestellungsdaten abzurufen:\
`SELECT DISTINCT base_currency_code FROM sales_order;`.
**HINWEIS: Dieser Befehl erfordert eine vollständige Tabellenüberprüfung. Bei Tabellen mit einer hohen Datensatzanzahl kann dies sich daher auf die Leistung auswirken, während die Abfrage ausgeführt wird**, um historische Auftragsdaten zu erhalten.
Wenn mehrere Basiswährungen jemals verwendet wurden, können Sie keine erweiterte Berichterstellung verwenden, da wir nur eine Währung unterstützen. Wenn in der Ausgabe nur eine Währung angezeigt wird, fahren Sie mit [Schritt 3](#step-3) fort.

+++

## Schritt 3: Überprüfen, ob die verwendete geteilte Datenbank verwendet wird {#step-3}

+++**Verwenden Sie eine aufgespaltete Datenbanklösung?**

Verwenden Sie [split database solution](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/storage/split-db/multi-master)?

a. YES - Verwenden Sie den Patch **MDVA-26831** im Fehler &quot;Erweiterte Berichterstellung 404&quot;für die Aufspaltungsdatenbanklösung und leeren Sie den Cache. Warten Sie 24 Stunden, bis der Auftrag erneut ausgeführt wird, und versuchen Sie es erneut.\
b. NO - Fahren Sie mit [Schritt 4](#step-4) fort.

+++

## Schritt 4: Bestätigen der Aktivierung der erweiterten Berichterstellung {#step-4}

+++**Ist die erweiterte Berichterstellung aktiviert?**

Überprüfen Sie **Admin** > **Stores** > **Einstellungen** > **Konfiguration** > **Allgemein** > **Fortschrittliche Berichterstellung**. Ausführliche Anweisungen finden Sie unter [Erweiterte Berichterstellung: Erweiterte Berichterstellung aktivieren](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting).

a. YES - Fahren Sie mit [Schritt 5](#step-5) fort.\
b. NO - [Aktivieren Sie die erweiterte Berichterstellung](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting), speichern und warten Sie 24 Stunden, bis Adobe Commerce und die erweiterte Berichterstellung synchronisiert werden. Überprüfen Sie, ob Ihre Daten jetzt geladen werden. Wenn es das Problem gelöst hat. Wenn nicht mit [Schritt 5](#step-5) fortgefahren wird.

+++

## Schritt 5: Auf Token suchen {#step-5}

+++**Gibt es ein Token?**

Vergewissern Sie sich, dass ein Token vorhanden ist, indem Sie die folgende Abfrage ausführen: `SELECT * FROM core_config_data WHERE path LIKE 'analytics/general/token' \G` Gibt es ein Token?

a. YES - Fahren Sie mit [Schritt 7](#step-7) fort.\
b. NO - Wenn der Tokenwert NULL ist oder sich kein Datensatz in der Datenbank befindet, fahren Sie mit [Schritt 6](#step-6) fort.

+++

## 6. Schritt - Zeile verwenden {#step-6}

+++**Gibt die Abfrage die Zeile zurück?**

Überprüfen Sie den Zählerwert in der Kennzeichnungstabelle, indem Sie diese Abfrage ausführen: ``SELECT * FROM `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter'\G`` Gibt die Abfrage die Zeile zurück?

a. JA - Gehen Sie wie folgt vor: 1. Führen Sie die folgende Abfrage aus:\
``DELETE from `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter';``\
2\. [Deaktivierung und Aktivierung des erweiterten Berichterstellungsmoduls](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting) in den Einstellungen und [Neuautorisierung des Tokens](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#verify-that-the-integration-is-active).\
3\. Warten Sie 24 Stunden, bis Adobe Commerce und die erweiterte Berichterstellung synchronisiert sind. Wenn Sie weiterhin keine Daten in der erweiterten Berichterstellung sehen können, senden Sie ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).[\
b. NO - Wenn die Abfrage nichts zurückgibt, gehen Sie wie folgt vor: 1. [Deaktivierung und Aktivierung des erweiterten Berichterstellungsmoduls](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting) in den Einstellungen und [Neuautorisierung des Tokens](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#verify-that-the-integration-is-active).\
2\. Warten Sie 24 Stunden, bis Adobe Commerce und die erweiterte Berichterstellung synchronisiert sind. Wenn Sie weiterhin keine Daten in der erweiterten Berichterstellung sehen können, senden Sie ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).[

+++

## Schritt 7: Auf Einträge in der Tabelle `cron_schedule` überprüfen {#step-7}

+++**Gibt es Datensätze in der Tabelle `cron_schedule`?**

Überprüfen Sie, ob der Auftrag `analytics_collect_data` ausgeführt wurde, indem Sie diese Abfrage ausführen: `SELECT * FROM cron_schedule WHERE job_code LIKE 'analytics_collect_data' \G`

a. YES - Wenn es Datensätze gibt und in der Spalte **Status** _ausgelassen_ steht, verwenden Sie den Patch in diesem KB-Artikel Update Advanced Reporting , um auf einer eigenen Cron-Gruppe auszuführen.\
b. JA - Wenn es Datensätze gibt und in der Spalte **status** _success_ steht, fahren Sie mit [Schritt 9](#step-9) fort.\
c. JA - Wenn Einträge vorhanden sind und in der Spalte **status** _error_ steht, fahren Sie mit [Schritt 8](#step-8) fort.\
d. NO - Wenn keine Datensätze vorhanden sind, fahren Sie mit [Schritt 8](#step-8) fort.

+++

## Schritt 8: Auf Auftrag in `support_report.log` suchen {#step-8}

+++**Wurde der Auftrag in `support_report.log` protokolliert?**

Führen Sie den Befehl aus: `zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz | tail`

a. YES - Wenn die Ausgabe aus der Abfrage einen erfolgreichen Auftrag anzeigt, z. B. `Cron Job analytics_collect_data is successfully finished`, fahren Sie mit [Schritt 9](#step-9) fort.\
b. NO - Wenn keine Datensätze im Protokoll vorhanden sind, senden [ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
c. JA - Wenn es Datensätze gibt, aber ein Fehler auftritt, fahren Sie mit [Schritt 10](#step-10) fort.

+++

## Schritt 9: Auf `data.tgz` Datei überprüfen {#step-9}

+++**Existiert die Datei `data.tgz` im System und sind Datensätze in den Zugriffsprotokollen enthalten?**

Um zu überprüfen, ob die Datei `data.tgz` vorhanden ist, führen Sie diesen Befehl aus. Er sollte Ordner mit Hash-Namen zurückgeben:

```
ls -ltr pub/media/analytics/
```

Um zu überprüfen, ob in access.logs Einträge vorhanden sind, führen Sie folgenden Befehl aus:

```
zgrep -i analytics /var/log/platform/[cluster_id|cluster_id_stg]/access.log* | grep MagentoBI
```

a. JA - Wenn die Datei &quot;`data.tgz`&quot; vorhanden ist und sich Datensätze in den Zugriffsprotokollen befinden, Sie aber dennoch einen 404-Fehler haben, müssen Sie [ein Support-Ticket senden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Fahren Sie mit [Schritt 10](#step-10) fort.

+++

## Schritt 10: Überprüfen der Fehlermeldung {#step-10}

+++**Gibt es eine Fehlermeldung, die vom Cron-Auftrag ausgegeben wird?**

Beispiel: In der Tabelle `core_config_data` wird der Fehler *Die Datei &quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a000850c0&quot;kann nicht gelöscht werden*. Warnung!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a000850c0?lang=en): Keine solche Datei oder Verzeichnis*

a. JA - Verwenden Sie den Patch ACSD-50165 in [Die Datei kann nicht gelöscht werden. Warnung!unlink: Kein solcher Datei- oder Verzeichnisfehler vom Admin](/help/troubleshooting/miscellaneous/file-cannot-be-deleated-no-file-or-directory.md), warten Sie 24 Stunden, bis der Auftrag erneut ausgeführt wird, und versuchen Sie es dann erneut.\
b. NO - Fahren Sie mit [Schritt 11](#step-11) fort.

+++

## Schritt 11: Überprüfen, ob der Fehler &quot;Seitenaufbau&quot;vorliegt {#step-11}

+++**Gibt es einen Fehler, der vom Seitenaufbau verursacht wurde?**

Beispiel: `report.ERROR: Cron Job analytics_collect_data has an error: substr_count() expects parameter 1 to be string, null given. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":224919552,"emalloc_start":216398384} [] []`

a. JA - Verwenden Sie den Patch MDVA-19391 in Common Advanced Reporting cron Auftragsmehlern in Adobe Commerce, warten Sie 24 Stunden, bis der Auftrag erneut ausgeführt wird, und versuchen Sie es erneut.\
b. NO - [ein Support-Ticket senden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Zurück zu Schritt 1](#step-1)

## Verwandtes Lesen

[Best Practices für die Änderung von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Playbook für die Commerce-Implementierung
