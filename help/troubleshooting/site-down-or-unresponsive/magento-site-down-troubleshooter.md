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

+++**Zeigt <https://status.adobe.com> Probleme an?**

a. YES - Wenn Sie [Adobe Magento-Status](https://status.adobe.com/products/3350) aktiviert haben und ein Problem angezeigt wurde, öffnen Sie ein [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) für weitere Untersuchungen.\
b. NO - Wenn Sie [Adobe Magento-Status](https://status.adobe.com/products/3350) aktiviert haben und kein Problem angezeigt wurde, fahren Sie mit [Schritt 2](#step-2) fort.

+++

## Schritt 2 {#step-2}

+++**Zeigt http://status.fastly.com Probleme an?**

a. YES - Wenn Sie [Fastly Status](https://status.fastly.com/) aktiviert haben und ein Problem angezeigt wurde, öffnen Sie ein [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) für weitere Untersuchungen.\
b. NO - Wenn Sie [Fastly Status](https://status.fastly.com/) aktiviert haben und kein Problem angezeigt wurde, fahren Sie mit [Schritt 3](#step-3) fort.

+++

## Schritt 3 {#step-3}

+++**Überprüfen Sie Ihre Website in einem Webbrowser. Erhalten Sie einen 200-Code (OK)?**

So prüfen Sie Fehlercodes in **Firefox**: Klicken Sie auf das Symbol **Menü öffnen** > **Web Developer** > **Tools ein-/ausschalten** > Registerkarte **Netzwerk** > Filter **Alle** > **Status** . So prüfen Sie die Fehlercodes in **Chrome**: Klicken Sie auf das Symbol **Menü öffnen** > **Weitere Tools** > **Entwicklertools** > Registerkarte **Netzwerk** > Filter **Alle** > Spalte **Status** .

a. JA - Öffnen Sie ein [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) für weitere Untersuchungen.\
b. NO - Fahren Sie mit [Schritt 4](#step-4) fort.

+++

## Schritt 4 {#step-4}

+++**Welchen Website-Fehlercode haben Sie erhalten?**

a. Fehler-Code 500 - Überprüfen Sie das Protokoll von `/var/log/platform/`. Wenn diese Daten Ihnen das Problem nicht zeigen, können Sie ein [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) öffnen und die Informationen zur Fehlerbehebung einschließen, die Sie bisher für weitere Untersuchungen haben.

b. Fehler-Code 503 - Überprüfen Sie das Protokoll von `var/reports`. Wenn diese Daten Ihnen das Problem nicht zeigen, können Sie ein [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) öffnen und die Informationen zur Fehlerbehebung einschließen, die Sie bisher für weitere Untersuchungen haben.

c. Fehler-Code 404 - Führen Sie die folgende Abfrage aus: `SELECT f.flag_data->>'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists FROM flag f LEFT JOIN staging_update su ON su.id = f.flag_data->>'$.current_version' WHERE flag_code = 'staging';` Wenn die Abfrage eine Tabelle zurückgibt, wobei der `update_exists`-Wert &quot;0&quot;ist, lesen Sie den Artikel [Fehler 404 auf allen Seiten, Storefront und Admin, da es beim Staging von Inhalten zu Problemen kommt](/help/troubleshooting/site-down-or-unresponsive/error-404-on-all-pages-due-to-content-staging-issue.md). In allen anderen Fällen gehen Sie zu [Schritt 5](#step-5).

d. Andere Fehlercodes: Fahren Sie mit [Schritt 5](#step-5) fort.

+++

## Schritt 5 {#step-5}

+++**Ist Ihre Site langsam oder weist hohe Server-Last, hohe CPU-Last, langsame Anforderungsverarbeitung oder Ausfälle in MySQL oder Redis auf?**

a. YES - Fahren Sie mit den Schritten für [Überprüfen auf DDOS-Angriffe von CLI](/help/troubleshooting/miscellaneous/checking-for-ddos-attack-from-cli.md) fort.\
b. NO - Überprüfen Sie die Protokolle `/var/log/exception.log` und `/var/log/deploy.log`. Wenn diese Daten Ihnen das Problem nicht darstellen, fahren Sie mit [Schritt 6](#step-6) fort.

+++

## Schritt 6 {#step-6}

+++**Haben Sie Bereitstellungsfehler oder Bereitstellungsfehler?**

a. YES - Fahren Sie mit [Schritt 13](#step-13) fort.\
b. NO - Fahren Sie mit [Schritt 7](#step-7) fort.

+++

## Schritt 7 {#step-7}

+++**Haben Sie Elasticsearch-Fehler?**

a. YES - Fahren Sie mit den Schritten zur Überprüfung von Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html) fort.[\
b. NO - Fahren Sie mit [Schritt 8](#step-8) fort.

+++

## Schritt 8 {#step-8}

+++**Hatte Ihre MySQL-Datenbank langsame Abfragen oder falsche Abfragen?**

a. YES - Fahren Sie mit [Überprüfen langsamer Abfragen und Prozesse in MySQL](/help/troubleshooting/database/checking-slow-queries-and-processes-mysql.md) fort und überprüfen Sie Ihre Abfragestruktur in diesem [MySQL-Abfrage-Tutorial](https://dev.mysql.com/doc/refman/5.5/en/entering-queries.html).\
b. NO - Fahren Sie mit [Schritt 9](#step-9) fort.

+++

## Schritt 9 {#step-9}

+++**Ist Ihr statischer Inhalt nicht verfügbar?**

a. YES - Fahren Sie mit dem Lesen des Artikels [Überprüfen des statischen Inhalts](https://support.magento.com/hc/en-us/articles/360031624091) fort.\
b. NO - Fahren Sie mit [Schritt 10](#step-10) fort.

+++

## Schritt 10 {#step-10}

+++**Sehen Sie in Ihren Logs PHP-Fatal-Fehler?**

a. YES - Fahren Sie mit der Beratung von [Häufigen PHP-Fatal-Fehlern und -Lösungen](/help/troubleshooting/miscellaneous/common-php-fatal-errors-and-solutions.md) fort.\
b. NO - Fahren Sie mit [Schritt 11](#step-11) fort.

+++

## Schritt 11 {#step-11}

+++**Haben Sie Redis-Fehler?**

a. YES - Fahren Sie mit den Schritten fort, um [sicherzustellen, dass Redis ausgeführt wird](https://devdocs.magento.com/guides/v2.3/config-guide/redis/redis-session.html#redis-verify), und um [Fehlerbehebung bei Redis](https://redis.io/topics/problems) durchzuführen.\
b. NO - Fahren Sie mit [Schritt 12](#step-12) fort.

+++

## Schritt 12 {#step-12}

+++**Werden Indexerfehler angezeigt?**

a. YES - Wenn Ihr Index durch einen anderen Prozess gesperrt ist, konsultieren Sie [Index wird durch einen anderen Prozess gesperrt](/help/troubleshooting/miscellaneous/index-is-locked-by-another-process.md). Wenn Sie andere Indexerfehler haben, öffnen Sie bitte ein [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), um weitere Informationen zu erhalten.\
b. NO - Öffnen Sie ein [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) für weitere Untersuchungen.

+++

## Schritt 13 {#step-13}

+++**Haben Sie Probleme mit Ihren benutzerdefinierten Modulen?**

a. YES - Lesen Sie weiterhin die Hilfe zur Fehlerbehebung bei benutzerspezifischen Modulen [Allgemeine Hilfe zur Fehlerbehebung bei benutzerspezifischen Modulen](/help/troubleshooting/miscellaneous/general-custom-module-troubleshooting-help.md).\
b. NO - Fahren Sie mit [Schritt 14](#step-14) fort.

+++

## Schritt 14 {#step-14}

+++**Haben Sie Post-Hook-Fehler?**

a. YES - Fahren Sie mit der Überprüfung Ihres MySQL-Fehlers in dieser [Referenz für MySQL-Server-Fehlermeldung](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html) fort.\
b. NO - Fahren Sie mit [Schritt 15](#step-15) fort.

+++

## Schritt 15 {#step-15}

+++**Haben Sie Probleme mit Composer-Patches?**

a. YES - Fahren Sie mit dem Consulting [Anwenden eines Patches fort, um Ihre Site herunterzufahren](/help/troubleshooting/site-down-or-unresponsive/applying-a-patch-takes-your-site-down.md).\
b. NO - Fahren Sie mit [Schritt 16](#step-16) fort.

+++

## Schritt 16 {#step-16}

+++**Haben Sie SQL-Datenbankfehler?**

a. YES - Fahren Sie mit der Überprüfung Ihres MySQL-Fehlers in dieser [Referenz für MySQL-Server-Fehlermeldung](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html) fort.\
b. NO - Fahren Sie mit [Schritt 17](#step-17) fort.

+++

## Schritt 17 {#step-17}

+++**Haben Sie Deaktivierung der MySQL-Datenbank oder eine nicht responsive MySQL-Datenbank?**

a. YES - Fahren Sie mit der Überprüfung auf MySQL-Deadlocks in diesem Artikel [Deadlocks in MySQL](/help/troubleshooting/database/deadlocks-in-mysql.md) fort.\
b. NO - Öffnen Sie ein [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) für weitere Untersuchungen.

+++

[Zurück zu Schritt 1](#step-1)

Klicken Sie auf [HERE](/help/troubleshooting/site-down-or-unresponsive/site-down-troubleshooting-diagram.md) , um das Diagramm zur Fehlerbehebung bei Site-Unten anzuzeigen.
