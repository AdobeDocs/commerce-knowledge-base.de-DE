---
title: Fehlerbehebung beim Herunterfahren der Adobe Commerce-Site
description: Klicken Sie auf die einzelnen Fragen, um die Antwortdetails in jedem Schritt der Fehlerbehebung anzuzeigen.
exl-id: 10a2313e-cc82-4ffc-9247-624884f3e165
feature: Support
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 0%

---

# Fehlerbehebung beim Herunterfahren der Adobe Commerce-Site

Klicken Sie auf die einzelnen Fragen, um die Antwortdetails in jedem Schritt der Fehlerbehebung anzuzeigen.

## Schritt 1 {#step-1}

+++**Zeigt <https://status.adobe.com> Probleme an?**

A. JA - Wenn Sie [Adobe Commerce-Status](https://status.adobe.com/cloud/experience_cloud) überprüft haben und ein Problem aufgetreten ist, öffnen Sie ein [Support-Ticket](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases), um weitere Nachforschungen anzustellen.\
b. NEIN - Wenn Sie [Adobe Commerce-Status](https://status.adobe.com/cloud/experience_cloud) aktiviert haben und kein Problem angezeigt wurde, fahren Sie mit [Schritt 2](#step-2) fort.

+++

## Schritt 2 {#step-2}

+++**Zeigt http://status.fastly.com Probleme an?**

A. JA - Wenn Sie [[!DNL Fastly] Status](https://status.fastly.com/) aktiviert haben und ein Problem angezeigt wird, öffnen Sie ein [Support-Ticket](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases), um weitere Untersuchungen durchzuführen.\
b. NEIN - Wenn Sie &quot;[[!DNL Fastly] &quot; aktiviert ](https://status.fastly.com/) und kein Problem angezeigt wurde, fahren Sie mit [Schritt 3](#step-3) fort.

+++

## Schritt 3 {#step-3}

+++**Überprüfen Sie Ihre Website in einem Webbrowser. Erhalten Sie einen 200-Code (OK)?**

Fehlercodes in **Firefox** überprüfen: Klicken Sie auf das **Menü öffnen**-Symbol > **Web-Entwickler** > **Tools ein/aus** > **Netzwerk**-Registerkarte > **Alle** Filter > **Status**. Fehlercodes in **Chrome** überprüfen: Klicken Sie auf das Symbol **Menü öffnen** > **Weitere Tools** > **Entwickler-Tools** > **Netzwerk** Registerkarte > **Alle** Filter > **Status**.

a. JA - Öffnen Sie ein [Support-Ticket](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) zur weiteren Untersuchung.\
b. NEIN - Fahren Sie mit [Schritt 4](#step-4) fort.

+++

## Schritt 4 {#step-4}

+++**Welchen Website-Fehler-Code haben Sie erhalten?**

a. Fehler-Code 500 - Protokoll von `/var/log/platform/` überprüfen. Wenn das Problem anhand dieser Daten nicht erkannt wird, können Sie ein [Support-Ticket](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) öffnen und die bisher verfügbaren Informationen zur Fehlerbehebung einbeziehen, um weitere Informationen zu erhalten.

b. Fehler-Code 503 - Protokoll von `var/reports` überprüfen. Wenn das Problem anhand dieser Daten nicht erkannt wird, können Sie ein [Support-Ticket](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) öffnen und die bisher verfügbaren Informationen zur Fehlerbehebung einbeziehen, um weitere Informationen zu erhalten.

c. Fehler-Code 404 - Führen Sie die folgende Abfrage aus: `SELECT f.flag_data->>'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists FROM flag f LEFT JOIN staging_update su ON su.id = f.flag_data->>'$.current_version' WHERE flag_code = 'staging';` Wenn die Abfrage eine Tabelle zurückgibt, bei der `update_exists` Wert „0“ ist, lesen Sie den Artikel [Fehler 404 auf allen Seiten, Storefront und Admin, aufgrund von Problemen mit der Inhalts-Staging](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/error-404-on-all-pages-due-to-content-staging-issue). Fahren Sie in allen anderen Fällen mit [Schritt 5](#step-5) fort.

d. Andere Fehlercodes: Fahren Sie mit [Schritt 5](#step-5) fort.

+++

## Schritt 5 {#step-5}

+++**Ist Ihre Site langsam oder weist sie eine hohe Server-Last, eine hohe CPU-Last, eine langsame Anforderungsverarbeitung oder Ausfälle in [!DNL MySQL] oder Redis auf?**

a. JA: Fahren Sie mit den Schritten für [Überprüfen auf DDOS-Angriffe von CLI](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-for-ddos-attack-from-cli) fort.\
b. NEIN - Überprüfen Sie die Protokolle von `/var/log/exception.log` und `/var/log/deploy.log`. Wenn diese Daten für Sie kein Problem darstellen, fahren Sie mit [Schritt 6](#step-6) fort.

+++

## Schritt 6 {#step-6}

+++**Haben Sie Bereitstellungsfehler oder einen Bereitstellungsfehler?**

a. JA - Mit [Schritt 13](#step-13) fortfahren.\
b. NEIN - Fahren Sie mit [Schritt 7](#step-7) fort.

+++

## Schritt 7 {#step-7}

+++**Haben Sie Elasticsearch-Fehler?**

a. JA: Fahren Sie mit den Schritten für [Überprüfen des Elasticsearchs ](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/search/configure-search-engine) fort.
b. NEIN - Fahren Sie mit [Schritt 8](#step-8) fort.

+++

## Schritt 8 {#step-8}

+++**Hatte Ihre [!DNL MySQL]-Datenbank langsame oder falsche Abfragen?**

a. JA - Fahren Sie mit dem Tutorial [Überprüfen langsamer Abfragen und Prozesse, die zu lange  [!DNL MySQL]](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql) and checking your query structure in this [[!DNL MySQL]  Abfragen dauern](https://dev.mysql.com/doc/refman/5.5/en/entering-queries.html) fort.\
b. NEIN - Fahren Sie mit [Schritt 9](#step-9) fort.

+++

## Schritt 9 {#step-9}

+++**Ist Ihr statischer Inhalt nicht verfügbar?**

a. JA - Konsultieren Sie den Artikel [Überprüfen statischer Inhalte](https://experienceleague.adobe.com/de/docs/commerce-operations/implementation-playbook/best-practices/development/static-content-deployment).\
b. NEIN - Mit [Schritt 10](#step-10) fortfahren.

+++

## Schritt 10 {#step-10}

+++**Werden in Ihren Protokollen schwerwiegende PHP-Fehler angezeigt?**

a. JA - Weiter zur Beratung [Häufige PHP-Fehler und -Lösungen](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/common-php-fatal-errors-and-solutions).\
b. NEIN - Mit [Schritt 11](#step-11) fortfahren.

+++

## Schritt 11 {#step-11}

+++**Werden Redis-Fehler angezeigt?**

a. JA: Fahren Sie mit den Schritten fort[ um zu überprüfen [!DNL Redis]  ob ](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/cache/redis/redis-session#verify-redis-connection) ausgeführt wird, und mit [[!DNL Redis] Fehlerbehebung](https://redis.io/topics/problems).\
b. NEIN - Mit [Schritt 12](#step-12) fortfahren.

+++

## Schritt 12 {#step-12}

+++**Werden Indexerfehler angezeigt?**

a. JA - Wenn Ihr Index durch einen anderen Prozess gesperrt ist, konsultieren Sie [Index ist durch einen anderen Prozess gesperrt](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/index-is-locked-by-another-process). Wenn Sie andere Indexerfehler haben, öffnen Sie ein [Support-Ticket](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases), um weitere Untersuchungen durchzuführen.\
b. NEIN - Öffnen Sie ein [Support-Ticket](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases), um weitere Untersuchungen durchzuführen.

+++

## Schritt 13 {#step-13}

+++**Haben Sie Probleme mit Ihren benutzerdefinierten Modulen?**

a. JA: Konsultieren Sie anschließend die [Hilfe zur Fehlerbehebung bei benutzerdefinierten Modulen](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/general-custom-module-troubleshooting-help).\
b. NEIN - Mit [Schritt 14](#step-14) fortfahren.

+++

## Schritt 14 {#step-14}

+++**Haben Sie Post-Hook-Fehler?**

a. JA: Fahren Sie mit der Überprüfung Ihres [!DNL MySQL] in dieser [[!DNL MySQL] Server-Fehlermeldungsreferenz) ](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b. NEIN - Mit [Schritt 15](#step-15) fortfahren.

+++

## Schritt 15 {#step-15}

+++**Haben Sie Probleme mit Composer-Patches?**

a. JA - Gehen Sie zur Beratung [Durch Anwenden eines Patches wird Ihre Site heruntergefahren](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/applying-a-patch-takes-your-site-down).\
b. NEIN - Mit [Schritt 16](#step-16) fortfahren.

+++

## Schritt 16 {#step-16}

+++**Haben Sie SQL-Datenbankfehler?**

a. JA: Fahren Sie mit der Überprüfung Ihres [!DNL MySQL] in dieser [[!DNL MySQL] Server-Fehlermeldungsreferenz) ](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b. NEIN - Mit [Schritt 17](#step-17) fortfahren.

+++

## Schritt 17 {#step-17}

+++**[!DNL MySQL] Haben Sie tote Sperren der Datenbank oder eine nicht reagierende [!DNL MySQL]-Datenbank?**

a. JA - Fahren Sie mit der Überprüfung auf [!DNL MySQL] Deadlocks in diesem Artikel [Deadlocks in [!DNL MySQL]](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/database/deadlocks-in-mysql) fort.\
b. NEIN - Öffnen Sie ein [Support-Ticket](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases), um weitere Untersuchungen durchzuführen.

+++

[Zurück zu Schritt 1](#step-1)

Klicken Sie [HIER](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/site-down-troubleshooting-diagram), um das Fehlerbehebungs-Flussdiagramm für die Site unten anzuzeigen.

## Verwandtes Lesen

[Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/de/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook
