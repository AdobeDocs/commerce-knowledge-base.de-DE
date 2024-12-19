---
title: Fehlerbehebung bei erweiterten Berichten für Adobe Commerce
description: Probleme mit erweiterten Berichten in Adobe Commerce können mit diesem Tool behoben werden. Dazu gehören erweiterte Berichte, die keine Daten und 404-Fehler anzeigen. Klicken Sie auf die einzelnen Fragen, um die Antwort in jedem Schritt der Fehlerbehebung anzuzeigen.
exl-id: 7ef9870c-b6b6-4144-a5a7-81aa20a1606c
feature: Cache, Support
role: Developer
source-git-commit: 3b402728be7a80b62f21319d2cf91a92f1ad4a0c
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 0%

---

# Fehlerbehebung bei erweiterten Berichten für Adobe Commerce

Probleme mit erweiterten Berichten in Adobe Commerce können mit diesem Tool behoben werden. Dazu gehören erweiterte Berichte, die keine Daten und 404-Fehler anzeigen. Klicken Sie auf die einzelnen Fragen, um die Antwort in jedem Schritt der Fehlerbehebung anzuzeigen.

## Schritt 1: Bestätigen, dass die Site die erweiterten Reporting-Anforderungen erfüllt {#step-1}

+++**Erfüllt Ihre Website die erweiterten Reporting-Anforderungen?**

Bei Verwendung der erweiterten Berichterstellung wird die Fehlerseite 404 angezeigt. Erfüllt Ihre Website [Advanced Reporting Requirements](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#requirements)?

a. JA - Mit [Schritt 2](#step-2) fortfahren.\
b. NEIN - Vervollständigen Sie die erweiterten Berichtsanforderungen für Ihre Site, indem Sie die Schritte unter [Erweiterte Berichtsanforderungen](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#requirements) befolgen. Fahren Sie dann mit ([ 2) ](#step-2).

+++

## Schritt 2: Gibt es Bestellungen in mehreren Basiswährungen? {#step-2}

+++**Werden mehrere Basiswährungen verwendet?**

Werden mehrere Basiswährungen verwendet (in Bestellungen und Konfiguration)? Führen Sie diesen [!DNL SQL] aus, um die aktuelle Konfiguration abzurufen: `SELECT value FROM core_config_data WHERE path = 'currency/options/base';` .

A. JA - Wenn von der Abfrage mehrere Zeilen zurückgegeben werden, können Sie keine erweiterten Berichte verwenden, da wir nur eine Währung unterstützen.\
b. NEIN - Ausgabe zeigt nur eine Währung. Beispiel: `USD`. Wurden bereits mehrere Basiswährungen (in Bestellungen) verwendet? Führen Sie diesen [!DNL SQL] aus, um historische Bestelldaten abzurufen:\
`SELECT DISTINCT base_currency_code FROM sales_order;`.
**HINWEIS: Dieser Befehl erfordert eine vollständige Tabellenüberprüfung. Bei Tabellen mit einer hohen Anzahl von Datensätzen kann dies daher während der Ausführung der Abfrage die Leistung beeinträchtigen,** historische Bestelldaten abzurufen.
Wenn bereits mehrere Basiswährungen verwendet wurden, können Sie keine erweiterten Berichte verwenden, da nur eine Währung unterstützt wird. Wenn die Ausgabe nur eine Währung anzeigt, fahren Sie mit [Schritt 3](#step-3) fort.

+++

## Schritt 3: Überprüfen, ob die geteilte Datenbank verwendet wird {#step-3}

+++**Verwenden Sie die Split-Datenbanklösung?**

Verwenden Sie die [Split-](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/storage/split-db/multi-master)?

a. JA - Verwenden Sie den Patch **MDVA-26831** in Advanced Reporting 404-Fehler bei der Lösung aufgeteilter Datenbanken und löschen Sie den Cache. Warten Sie 24 Stunden, bis der Auftrag erneut ausgeführt wird, und versuchen Sie es dann erneut.\
b. NEIN - Fahren Sie mit [Schritt 4](#step-4) fort.

+++

## Schritt 4: Bestätigen der Aktivierung des erweiterten Reportings {#step-4}

+++**Ist die erweiterte Berichterstellung aktiviert?**

Überprüfen Sie **Admin** > **Stores** > **Einstellungen** > **Konfiguration** > **Allgemein** > **Erweiterte Berichterstellung**. Ausführliche Anweisungen finden Sie unter [Erweiterte Berichterstellung: Erweiterte Berichterstellung aktivieren](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting).

a. JA - Mit [Schritt 5](#step-5) fortfahren.\
b. NEIN - [Erweiterte Berichterstellung aktivieren](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting) und 24 Stunden warten, bis Adobe Commerce und die erweiterten Berichterstellung synchronisiert werden. Überprüfen Sie, ob Ihre Daten jetzt geladen werden. Wenn dies der Fall ist, haben Sie das Problem gelöst. Wenn nicht mit (Schritt [) ](#step-5) wird.

+++

## Schritt 5: Token suchen {#step-5}

+++**Gibt es ein Token?**

Vergewissern Sie sich, dass ein Token vorhanden ist, indem Sie die folgende Abfrage ausführen: `SELECT * FROM core_config_data WHERE path LIKE 'analytics/general/token' \G` Gibt es ein Token?

a. JA - Mit [Schritt 7](#step-7) fortfahren.\
b. NEIN - Wenn der Token-Wert NULL ist oder es keinen Datensatz in der Datenbank gibt, fahren Sie mit [Schritt 6](#step-6) fort.

+++

## Schritt 6: Verwenden der Zeile {#step-6}

+++**Gibt die Abfrage die Zeile zurück?**

Überprüfen Sie den Zählerwert in der Flag-Tabelle, indem Sie diese Abfrage ausführen: ``SELECT * FROM `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter'\G`` Gibt die Abfrage die Zeile zurück?

a. JA - Führen Sie folgende Schritte durch: 1. Führen Sie die folgende Abfrage aus:\
``DELETE from `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter';``\
2\ [Deaktivieren und Aktivieren des erweiterten Reporting-Moduls](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting) in den Einstellungen und [autorisieren Sie das Token erneut](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#verify-that-the-integration-is-active).\
3\ Warten Sie 24 Stunden, bis Adobe Commerce und Advanced Reporting synchronisiert sind. Wenn Sie im erweiterten Reporting immer noch keine Daten sehen können, [ Sie ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NEIN - Wenn die Abfrage nichts zurückgibt, führen Sie die folgenden Schritte aus: 1. [Deaktivieren und Aktivieren des erweiterten Reporting-Moduls](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting) in den Einstellungen und [autorisieren Sie das Token erneut](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#verify-that-the-integration-is-active).\
2\ Warten Sie 24 Stunden, bis Adobe Commerce und Advanced Reporting synchronisiert sind. Wenn Sie im erweiterten Reporting immer noch keine Daten sehen können, [ Sie ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Schritt 7: Prüfen auf Datensätze in `cron_schedule` Tabelle {#step-7}

+++**Gibt es Datensätze in der `cron_schedule`?**

Vergewissern Sie sich, dass die `analytics_collect_data` ausgeführt wurde, indem Sie diese Abfrage ausführen: `SELECT * FROM cron_schedule WHERE job_code LIKE 'analytics_collect_data' \G`

A. JA - Wenn Datensätze vorhanden sind und in der Spalte **status** der Wert &quot;_missing_ angegeben ist, verwenden Sie den Patch in diesem KB-Artikel Aktualisieren der erweiterten Berichterstellung, um die Ausführung auf einer eigenen Cron-Gruppe durchzuführen.\
b. JA - Wenn Datensätze vorhanden sind und die Spalte **status** den Wert _success_ aufweist, fahren Sie mit [Schritt 9](#step-9) fort.\
c. JA - Wenn Datensätze vorhanden sind und die Spalte **status** den Wert _error_ aufweist, fahren Sie mit [Schritt 8.](#step-8) fort.\
d. NEIN - Wenn keine Datensätze vorhanden sind, fahren Sie mit ([) ](#step-8).

+++

## Schritt 8: In `support_report.log` nach Arbeit suchen {#step-8}

+++**Wurde der Auftrag `support_report.log` angemeldet?**

Führen Sie den folgenden Befehl aus: `zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz | tail`

a. JA - Wenn die Ausgabe der Abfrage auf einen erfolgreichen Auftrag hinweist, fahren `Cron Job analytics_collect_data is successfully finished` beispielsweise mit ([ 9) ](#step-9).\
b. NEIN - Wenn das Protokoll keine Datensätze enthält, [ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
c. JA - Wenn Datensätze vorhanden sind, aber ein Fehler auftritt, fahren Sie mit [Schritt 10](#step-10) fort.

+++

## 9. Schritt - Auf `data.tgz` Datei prüfen {#step-9}

+++**Ist die Datei `data.tgz` im System vorhanden und gibt es Einträge in den Zugriffsprotokollen?**

Um zu überprüfen, ob die Datei `data.tgz` vorhanden ist, führen Sie diesen Befehl aus. Es sollten Ordner mit Hash-Namen zurückgegeben werden:

```
ls -ltr pub/media/analytics/
```

Um zu überprüfen, ob Einträge in „access.logs“ vorhanden sind, führen Sie diesen Befehl aus:

```
zgrep -i analytics /var/log/platform/[cluster_id|cluster_id_stg]/access.log* | grep MagentoBI
```

A. JA - Wenn die `data.tgz` vorhanden ist und Einträge in den Zugriffsprotokollen vorhanden sind, aber weiterhin der Fehler 404 auftritt, müssen Sie [ein Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NEIN - Mit [Schritt 10](#step-10) fortfahren.

+++

## Schritt 10: Fehlermeldung überprüfen {#step-10}

+++**Gibt es eine Fehlermeldung, die vom Cron-Auftrag ausgelöst wird?**

Beispiel: In der `core_config_data` wird der Fehler angezeigt *Die Datei &quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0 kann nicht gelöscht werden*. Warnung!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0?lang=de): Keine derartige Datei oder derartiges Verzeichnis*

a. JA - Verwenden Sie den Patch ACSD-50165 in [Die Datei kann nicht gelöscht werden. Warnung!Verknüpfung aufheben: Keine Datei- oder Verzeichnisfehler vom Admin](/help/troubleshooting/miscellaneous/file-cannot-be-deleated-no-file-or-directory.md), 24 Stunden warten, bis der Auftrag erneut ausgeführt wird, und dann erneut versuchen.\
b. NEIN - Mit [Schritt 11](#step-11) fortfahren.

+++

## Schritt 11: Überprüfen, ob ein Page Builder-Fehler vorliegt {#step-11}

+++**Gibt es einen Fehler, der von Page Builder verursacht wird?**

Beispiel: `report.ERROR: Cron Job analytics_collect_data has an error: substr_count() expects parameter 1 to be string, null given. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":224919552,"emalloc_start":216398384} [] []`

A. JA - Verwenden Sie den MDVA-19391-Patch in Allgemeine CRON-Auftragsfehler des erweiterten Reportings in Adobe Commerce. Warten Sie 24 Stunden, bis der Auftrag erneut ausgeführt wird, und versuchen Sie es erneut.\
b. NEIN - [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Zurück zu Schritt 1](#step-1)

## Verwandtes Lesen

[Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook
