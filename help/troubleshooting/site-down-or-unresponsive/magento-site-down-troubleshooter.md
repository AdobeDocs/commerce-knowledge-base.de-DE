---
title: Fehlerbehebung auf der Adobe Commerce-Site
description: Klicken Sie auf jede Frage, um die Antwortdetails bei jedem Schritt der Problembehebung anzuzeigen.
exl-id: 10a2313e-cc82-4ffc-9247-624884f3e165
feature: Support
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 0%

---

# Fehlerbehebung auf der Adobe Commerce-Site

Klicken Sie auf jede Frage, um die Antwortdetails bei jedem Schritt der Problembehebung anzuzeigen.

## Schritt 1 {#step-1}

+++**Does <https://status.adobe.com> Probleme anzeigen?**

a. JA - Wenn Sie die Option [Adobe Magento-Status](https://status.adobe.com/products/3350) und zeigte ein Problem an, öffnen Sie eine [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) für weitere Untersuchungen.\
b. NO - Wenn Sie [Adobe Magento-Status](https://status.adobe.com/products/3350) und es wurde kein Problem angezeigt, fahren Sie mit [Schritt 2](#step-2).

+++

## Schritt 2 {#step-2}

+++**Zeigt http://status.fastly.com Probleme an?**

a. JA - Wenn Sie die Option [Fastly Status](https://status.fastly.com/) und zeigte ein Problem an, öffnen Sie eine [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) für weitere Untersuchungen.\
b. NO - Wenn Sie [Fastly Status](https://status.fastly.com/) und es wurde kein Problem angezeigt, fahren Sie mit [Schritt 3](#step-3).

+++

## Schritt 3 {#step-3}

+++**Überprüfen Sie Ihre Website in einem Webbrowser. Haben Sie einen 200-Code (OK)?**

So prüfen Sie Fehlercodes in **Firefox**: Klicken Sie auf die **Menü öffnen** Symbol > **Webentwickler** > **Umschalten zwischen Tools** > **Netzwerk** tab > **Alle** filter > **Status** Spalte. So prüfen Sie Fehlercodes in **Chrome**: Klicken Sie auf die **Menü öffnen** Symbol > **Weitere Tools** > **Entwicklertools** > **Netzwerk** tab > **Alle** filter > **Status** Spalte.

a. JA - Öffnen Sie eine [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) für weitere Untersuchungen.\
b. NO - Fahren Sie mit [Schritt 4](#step-4).

+++

## Schritt 4 {#step-4}

+++**Welchen Website-Fehlercode hast du erhalten?**

a. Fehler-Code 500 - Überprüfen des Protokolls von `/var/log/platform/`. Wenn diese Daten Ihnen das Problem nicht darstellen, können Sie eine [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) und enthalten die Informationen zur Fehlerbehebung, die Sie bisher für weitere Untersuchungen haben.

b. Fehlercode 503 - Überprüfen des Protokolls von `var/reports`. Wenn diese Daten Ihnen das Problem nicht darstellen, können Sie eine [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) und enthalten die Informationen zur Fehlerbehebung, die Sie bisher für weitere Untersuchungen haben.

c. Fehler-Code 404 - Führen Sie die folgende Abfrage aus: `SELECT f.flag_data->>'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists FROM flag f LEFT JOIN staging_update su ON su.id = f.flag_data->>'$.current_version' WHERE flag_code = 'staging';` Wenn die Abfrage eine Tabelle zurückgibt, wobei `update_exists` den Wert &quot;0&quot;hat, siehe [Fehler 404 auf allen Seiten, Storefront und Administrator aufgrund des Problems mit der Inhaltstaging-Umgebung](/help/troubleshooting/site-down-or-unresponsive/error-404-on-all-pages-due-to-content-staging-issue.md) Artikel. In allen anderen Fällen wird [Schritt 5](#step-5).

d. Andere Fehlercodes - fahren Sie mit [Schritt 5](#step-5).

+++

## Schritt 5 {#step-5}

+++**Ist Ihre Site langsam oder weist hohe Server-Last, hohe CPU-Last, langsame Anforderungsverarbeitung oder Ausfälle in MySQL oder Redis auf?**

a. YES - Fahren Sie mit den Schritten für [Überprüfung auf DDOS-Angriffe über CLI](/help/troubleshooting/miscellaneous/checking-for-ddos-attack-from-cli.md).\
b. NO - Protokolle der `/var/log/exception.log` und `/var/log/deploy.log`und wenn diese Daten Ihnen das Problem nicht darstellen, fahren Sie mit dem [Schritt 6](#step-6).

+++

## Schritt 6 {#step-6}

+++**Haben Sie Bereitstellungsfehler oder Bereitstellungsfehler?**

a. JA - fahren Sie mit [Schritt 13](#step-13).\
b. NO - Fahren Sie mit [Schritt 7](#step-7).

+++

## Schritt 7 {#step-7}

+++**Haben Sie Elasticsearch-Fehler?**

a. YES - Fahren Sie mit den Schritten für [Elasticsearch überprüfen](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html).\
b. NO - Fahren Sie mit [Schritt 8](#step-8).

+++

## Schritt 8 {#step-8}

+++**Hatte Ihre MySQL-Datenbank langsame Abfragen oder falsche Abfragen?**

a. JA - Fortfahren mit [Überprüfen langsamer Abfragen und Prozesse, die in MySQL zu lange dauern](/help/troubleshooting/database/checking-slow-queries-and-processes-mysql.md) und die Abfragestruktur in diesem [MySQL-Abfrage-Tutorial](https://dev.mysql.com/doc/refman/5.5/en/entering-queries.html).\
b. NO - Fahren Sie mit [Schritt 9](#step-9).

+++

## Schritt 9 {#step-9}

+++**Ist Ihr statischer Inhalt nicht verfügbar?**

a. JA - Fahren Sie mit der Beratung der [Überprüfen statischer Inhalte](https://support.magento.com/hc/en-us/articles/360031624091) Artikel.\
b. NO - Fahren Sie mit [Schritt 10](#step-10).

+++

## Schritt 10 {#step-10}

+++**Sehen Sie in Ihren Logs PHP Fatal Errors?**

a. JA - Fortsetzung der Beratung [Häufige Fehler und Lösungen bei PHP](/help/troubleshooting/miscellaneous/common-php-fatal-errors-and-solutions.md).\
b. NO - Fahren Sie mit [Schritt 11](#step-11).

+++

## Schritt 11 {#step-11}

+++**Werden Ihnen Redis-Fehler angezeigt?**

a. YES - Fahren Sie mit den Schritten fort, um [Überprüfen, ob Redis ausgeführt wird](https://devdocs.magento.com/guides/v2.3/config-guide/redis/redis-session.html#redis-verify) und [Fehlerbehebung bei Dias](https://redis.io/topics/problems).\
b. NO - Fahren Sie mit [Schritt 12](#step-12).

+++

## Schritt 12 {#step-12}

+++**Werden Indexerfehler angezeigt?**

a. JA - Wenn Ihr Index durch einen anderen Prozess gesperrt ist, konsultieren Sie [Index wird durch einen anderen Prozess gesperrt](/help/troubleshooting/miscellaneous/index-is-locked-by-another-process.md). Wenn Sie andere Indexerfehler haben, öffnen Sie bitte eine [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) für weitere Untersuchungen.\
b. NO - Öffnen Sie eine [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) für weitere Untersuchungen.

+++

## Schritt 13 {#step-13}

+++**Haben Sie Probleme mit Ihren benutzerdefinierten Modulen?**

a. JA - Konsultieren Sie [Allgemeine Hilfe zur Fehlerbehebung bei benutzerdefinierten Modulen](/help/troubleshooting/miscellaneous/general-custom-module-troubleshooting-help.md).\
b. NO - Fahren Sie mit [Schritt 14](#step-14).

+++

## Schritt 14 {#step-14}

+++**Haben Sie Post-Hook-Fehler?**

a. YES - Überprüfen Sie Ihren MySQL-Fehler in diesem [Referenz zu MySQL-Server-Fehlermeldungen](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b. NO - Fahren Sie mit [Schritt 15](#step-15).

+++

## Schritt 15 {#step-15}

+++**Haben Sie Probleme mit Composer-Patches?**

a. JA - zur Beratung übergehen [Durch Anwenden eines Pflasters wird Ihre Website heruntergefahren](/help/troubleshooting/site-down-or-unresponsive/applying-a-patch-takes-your-site-down.md).\
b. NO - Fahren Sie mit [Schritt 16](#step-16).

+++

## Schritt 16 {#step-16}

+++**Haben Sie SQL-Datenbankfehler?**

a. YES - Überprüfen Sie Ihren MySQL-Fehler in diesem [Referenz zu MySQL-Server-Fehlermeldungen](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b. NO - Fahren Sie mit [Schritt 17](#step-17).

+++

## Schritt 17 {#step-17}

+++**Haben Sie Deaktivierung der MySQL-Datenbank oder eine nicht responsive MySQL-Datenbank?**

a. YES - Fahren Sie mit der Überprüfung auf MySQL-Deadlock-Sperren hier fort. [Deadlocks in MySQL](/help/troubleshooting/database/deadlocks-in-mysql.md) Artikel.\
b. NO - Öffnen Sie eine [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) für weitere Untersuchungen.

+++

[Zurück zu Schritt 1](#step-1)

Klicks [HIER](/help/troubleshooting/site-down-or-unresponsive/site-down-troubleshooting-diagram.md) um das Diagramm zur Fehlerbehebung bei Site-Down zu sehen.
