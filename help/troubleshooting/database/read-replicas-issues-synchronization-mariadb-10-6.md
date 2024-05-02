---
title: Replikat-Probleme in Adobe Commerce Cloud 2.4.6 mit MariaDB 10.6 lesen
description: In diesem Artikel wird beschrieben, wie Sie Replikat-Probleme in Adobe Commerce Cloud 2.4.6 mit MariaDB 10.6 beheben können.
feature: Configuration
role: Developer,Admin
exl-id: b7af1cc3-93ff-40c5-8959-076cedddb56d
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---

# Replikat-Probleme in Adobe Commerce Cloud 2.4.6 mit MariaDB 10.6 lesen

Dieser Artikel bietet Lösungen für unerwartetes Verhalten bei der Verwendung von Read Replikat auf Adobe Commerce Cloud 2.4.6 mit MariaDB 10.6+.

## Betroffene Produkte und Versionen

* MariaDB 10.6+
* Adobe Commerce in Cloud-Infrastruktur 2.4.6

## Problem

Nicht kritische Lesevorgänge zeigen falsche Informationen an.

## Ursache

Die `slave_parallel_mode` Die Konfiguration in der Datenbank wurde standardmäßig in *optimistics* wann der Wert sein sollte *konservativ* und die `synchronous_replication` -Wert in Ece-Tools standardmäßig auf *true* wann der Wert sein sollte *false*.

## Lösung

1. Stellen Sie sicher, dass die `slave_parallel_mode` -Parameter auf *konservativ* (Sie müssen [Support-Ticket erstellen](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) wenn der Wert nicht als *konservativ*). Führen Sie zum Überprüfen den folgenden Befehl aus:

   ```
    MariaDB [main]> show variables like 'slave_parallel_mode';
    +---------------------+--------------+
    | Variable_name       | Value        |
    +---------------------+--------------+
    | slave_parallel_mode | conservative |
    +---------------------+--------------+
    1 row in set (0.001 sec)
   ```

1. Aktualisieren `.magento.env.yaml` Datenbankkonfigurationen für:

   ```yaml
       DATABASE_CONFIGURATION:
        _merge: true
           slave_connection:
               default:
                   synchronous_replication: false
   ```



Anweisungen zum Aktualisieren der Datenbankkonfiguration finden Sie unter [DATABASE_CONFIGURATION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#database_configuration) im Thema Variablen bereitstellen im Commerce on Cloud Infrastructure-Handbuch.


## Verwandtes Lesen

* [Umgebungsvariablen für die Bereitstellung konfigurieren](/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) im Commerce on Cloud Infrastructure Guide.
* [Best Practices für die Datenbankkonfiguration](/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) im Playbook für Implementierungen.
