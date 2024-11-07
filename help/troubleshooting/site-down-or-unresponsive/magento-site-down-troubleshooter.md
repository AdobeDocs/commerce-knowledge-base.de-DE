---
title: Fehlerbehebung auf der Adobe Commerce-Site
description: Klicken Sie auf jede Frage, um die Antwortdetails bei jedem Schritt der Problembehebung anzuzeigen.
exl-id: 10a2313e-cc82-4ffc-9247-624884f3e165
feature: Support
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 0%

---

# Fehlerbehebung auf der Adobe Commerce-Site

Klicken Sie auf jede Frage, um die Antwortdetails bei jedem Schritt der Problembehebung anzuzeigen.

## Schritt 1 {#step-1}

+++**Zeigt <https://status.adobe.com> Probleme an?**

a. JA - Wenn Sie [Adobe Commerce-Status](https://status.adobe.com/cloud/experience_cloud) aktiviert haben und ein Problem angezeigt wurde, öffnen Sie ein [Support-Ticket](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) für weitere Untersuchungen.\
b. NO - Wenn Sie [Adobe Commerce-Status](https://status.adobe.com/cloud/experience_cloud) aktiviert haben und kein Problem angezeigt wurde, fahren Sie mit [Schritt 2](#step-2) fort.

+++

## Schritt 2 {#step-2}

+++**Zeigt http://status.fastly.com Probleme an?**

a. JA - Wenn Sie [[!DNL Fastly] Status](https://status.fastly.com/) aktiviert haben und ein Problem angezeigt wurde, öffnen Sie ein [Support-Ticket](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) für weitere Untersuchungen.\
b. NO - Wenn Sie [[!DNL Fastly] Status](https://status.fastly.com/) aktiviert haben und kein Problem angezeigt wurde, fahren Sie mit [Schritt 3](#step-3) fort.

+++

## Schritt 3 {#step-3}

+++**Überprüfen Sie Ihre Website in einem Webbrowser. Erhalten Sie einen 200-Code (OK)?**

So prüfen Sie Fehlercodes in **Firefox**: Klicken Sie auf das Symbol **Menü öffnen** > **Web Developer** > **Tools ein-/ausschalten** > Registerkarte **Netzwerk** > Filter **Alle** > **Status** . So prüfen Sie die Fehlercodes in **Chrome**: Klicken Sie auf das Symbol **Menü öffnen** > **Weitere Tools** > **Entwicklertools** > Registerkarte **Netzwerk** > Filter **Alle** > Spalte **Status** .

a. JA - Öffnen Sie ein [Support-Ticket](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) für weitere Untersuchungen.\
b. NO - Fahren Sie mit [Schritt 4](#step-4) fort.

+++

## Schritt 4 {#step-4}

+++**Welchen Website-Fehlercode haben Sie erhalten?**

a. Fehler-Code 500 - Überprüfen Sie das Protokoll von `/var/log/platform/`. Wenn diese Daten Ihnen das Problem nicht zeigen, können Sie ein [Support-Ticket](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) öffnen und die Informationen zur Fehlerbehebung einschließen, die Sie bisher für weitere Untersuchungen haben.

b. Fehler-Code 503 - Überprüfen Sie das Protokoll von `var/reports`. Wenn diese Daten Ihnen das Problem nicht zeigen, können Sie ein [Support-Ticket](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) öffnen und die Informationen zur Fehlerbehebung einschließen, die Sie bisher für weitere Untersuchungen haben.

c. Fehler-Code 404 - Führen Sie die folgende Abfrage aus: `SELECT f.flag_data->>'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists FROM flag f LEFT JOIN staging_update su ON su.id = f.flag_data->>'$.current_version' WHERE flag_code = 'staging';` Wenn die Abfrage eine Tabelle zurückgibt, wobei der `update_exists`-Wert &quot;0&quot;ist, lesen Sie den Artikel [Fehler 404 auf allen Seiten, Storefront und Admin, da es beim Staging von Inhalten zu Problemen kommt](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/error-404-on-all-pages-due-to-content-staging-issue). In allen anderen Fällen gehen Sie zu [Schritt 5](#step-5).

d. Andere Fehlercodes: Fahren Sie mit [Schritt 5](#step-5) fort.

+++

## Schritt 5 {#step-5}

+++**Ist Ihre Site langsam oder weist hohe Server-Last, hohe CPU-Last, langsame Anforderungsverarbeitung oder Ausfälle in [!DNL MySQL] oder Redis auf?**

a. YES - Fahren Sie mit den Schritten für [Überprüfen auf DDOS-Angriffe von CLI](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-for-ddos-attack-from-cli) fort.\
b. NO - Überprüfen Sie die Protokolle `/var/log/exception.log` und `/var/log/deploy.log`. Wenn diese Daten Ihnen das Problem nicht darstellen, fahren Sie mit [Schritt 6](#step-6) fort.

+++

## Schritt 6 {#step-6}

+++**Haben Sie Bereitstellungsfehler oder Bereitstellungsfehler?**

a. YES - Fahren Sie mit [Schritt 13](#step-13) fort.\
b. NO - Fahren Sie mit [Schritt 7](#step-7) fort.

+++

## Schritt 7 {#step-7}

+++**Haben Sie Elasticsearch-Fehler?**

a. YES - Fahren Sie mit den Schritten zur Überprüfung von Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/configure-search-engine) fort.
[
b. NO - Fahren Sie mit [Schritt 8](#step-8) fort.

+++

## Schritt 8 {#step-8}

+++**Hatte Ihre [!DNL MySQL]-Datenbank langsame Abfragen oder falsche Abfragen?**

a. YES - Fahren Sie mit [Überprüfen langsamer Abfragen und Prozesse, die zu lange dauern, im [!DNL MySQL]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql) and checking your query structure in this [[!DNL MySQL] Abfrage-Tutorial](https://dev.mysql.com/doc/refman/5.5/en/entering-queries.html) fort.\
b. NO - Fahren Sie mit [Schritt 9](#step-9) fort.

+++

## Schritt 9 {#step-9}

+++**Ist Ihr statischer Inhalt nicht verfügbar?**

a. YES - Fahren Sie mit dem Lesen des Artikels [Überprüfen des statischen Inhalts](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/static-content-deployment) fort.\
b. NO - Fahren Sie mit [Schritt 10](#step-10) fort.

+++

## Schritt 10 {#step-10}

+++**Sehen Sie in Ihren Logs PHP-Fatal-Fehler?**

a. YES - Fahren Sie mit der Beratung von [Häufigen PHP-Fatal-Fehlern und -Lösungen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/common-php-fatal-errors-and-solutions) fort.\
b. NO - Fahren Sie mit [Schritt 11](#step-11) fort.

+++

## Schritt 11 {#step-11}

+++**Haben Sie Redis-Fehler?**

a. YES - Fahren Sie mit den Schritten fort, um [sicherzustellen, dass [!DNL Redis] ausgeführt wird](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/redis/redis-session#verify-redis-connection), und um [[!DNL Redis] Fehlerbehebung](https://redis.io/topics/problems) durchzuführen.\
b. NO - Fahren Sie mit [Schritt 12](#step-12) fort.

+++

## Schritt 12 {#step-12}

+++**Werden Indexerfehler angezeigt?**

a. YES - Wenn Ihr Index durch einen anderen Prozess gesperrt ist, konsultieren Sie [Index wird durch einen anderen Prozess gesperrt](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/index-is-locked-by-another-process). Wenn Sie andere Indexerfehler haben, öffnen Sie bitte ein [Support-Ticket](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases), um weitere Informationen zu erhalten.\
b. NO - Öffnen Sie ein [Support-Ticket](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) für weitere Untersuchungen.

+++

## Schritt 13 {#step-13}

+++**Haben Sie Probleme mit Ihren benutzerdefinierten Modulen?**

a. YES - Lesen Sie weiterhin die Hilfe zur Fehlerbehebung bei benutzerspezifischen Modulen [Allgemeine Hilfe zur Fehlerbehebung bei benutzerspezifischen Modulen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/general-custom-module-troubleshooting-help).\
b. NO - Fahren Sie mit [Schritt 14](#step-14) fort.

+++

## Schritt 14 {#step-14}

+++**Haben Sie Post-Hook-Fehler?**

a. YES - Fahren Sie mit der Überprüfung Ihres [!DNL MySQL]-Fehlers in dieser Referenz mit der [[!DNL MySQL] Serverfehlermeldung](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html) fort.\
b. NO - Fahren Sie mit [Schritt 15](#step-15) fort.

+++

## Schritt 15 {#step-15}

+++**Haben Sie Probleme mit Composer-Patches?**

a. YES - Fahren Sie mit dem Consulting [Anwenden eines Patches fort, um Ihre Site herunterzufahren](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/applying-a-patch-takes-your-site-down).\
b. NO - Fahren Sie mit [Schritt 16](#step-16) fort.

+++

## Schritt 16 {#step-16}

+++**Haben Sie SQL-Datenbankfehler?**

a. YES - Fahren Sie mit der Überprüfung Ihres [!DNL MySQL]-Fehlers in dieser Referenz mit der [[!DNL MySQL] Serverfehlermeldung](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html) fort.\
b. NO - Fahren Sie mit [Schritt 17](#step-17) fort.

+++

## Schritt 17 {#step-17}

+++**Haben Sie [!DNL MySQL] Datenbanksperre oder eine nicht responsive [!DNL MySQL] Datenbank?**

a. YES - Fahren Sie mit der Überprüfung auf [!DNL MySQL] Deadlocks in diesem Artikel [Deadlocks in [!DNL MySQL]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/database/deadlocks-in-mysql) fort.\
b. NO - Öffnen Sie ein [Support-Ticket](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) für weitere Untersuchungen.

+++

[Zurück zu Schritt 1](#step-1)

Klicken Sie auf [HERE](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/site-down-troubleshooting-diagram) , um das Diagramm zur Fehlerbehebung bei Site-Unten anzuzeigen.

## Verwandtes Lesen

[Best Practices für die Änderung von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Playbook für die Commerce-Implementierung
