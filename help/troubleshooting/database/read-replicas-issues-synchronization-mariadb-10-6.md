---
title: Lesen Sie Replikat-Probleme in Adobe Commerce Cloud 2.4.6 mit MariaDB 10.6
description: In diesem Artikel wird erläutert, wie Sie Probleme mit "Replikat lesen“ in Adobe Commerce Cloud 2.4.6 mit MariaDB 10.6 beheben können.
feature: Configuration
role: Developer,Admin
exl-id: b7af1cc3-93ff-40c5-8959-076cedddb56d
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---

# Lesen Sie Replikat-Probleme in Adobe Commerce Cloud 2.4.6 mit MariaDB 10.6

Dieser Artikel bietet Lösungen für unerwartetes Verhalten bei der Verwendung von Read Replikat in Adobe Commerce Cloud 2.4.6 mit MariaDB 10.6+.

## Betroffene Produkte und Versionen

* MariaDB 10.6+
* Adobe Commerce auf Cloud-Infrastruktur 2.4.6

## Problem

Nicht kritische Lesevorgänge zeigen falsche Informationen an.

## Ursache

Die `slave_parallel_mode` in der Datenbank wurde standardmäßig in &quot;*&quot; geändert* wenn der Wert *konservativ* sein sollte, und der `synchronous_replication` in Ece-Tools ist standardmäßig auf *true* eingestellt, wenn der Wert *false* sein sollte.

## Lösung

1. Vergewissern Sie sich, dass der Parameter `slave_parallel_mode` auf *Konservativ* gesetzt ist (Sie müssen [ein Support-Ticket erstellen](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) wenn der Wert nicht als *Konservativ*). Führen Sie zum Überprüfen den folgenden Befehl aus:

   ```
    MariaDB [main]> show variables like 'slave_parallel_mode';
    +---------------------+--------------+
    | Variable_name       | Value        |
    +---------------------+--------------+
    | slave_parallel_mode | conservative |
    +---------------------+--------------+
    1 row in set (0.001 sec)
   ```

1. Aktualisieren Sie `.magento.env.yaml` Datenbankkonfigurationen, um:

   ```yaml
       DATABASE_CONFIGURATION:
        _merge: true
           slave_connection:
               default:
                   synchronous_replication: false
   ```



Anweisungen zum Aktualisieren der Datenbankkonfiguration finden Sie unter [DATABASE_CONFIGURATION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#database_configuration) im Thema Variablen bereitstellen im Handbuch Commerce on Cloud Infrastructure .


## Verwandtes Lesen

* [Konfigurieren von Umgebungsvariablen für die Bereitstellung](/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) im Handbuch zu Commerce in Cloud-Infrastrukturen .
* [Best Practices für die Datenbankkonfiguration](/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) im Implementation Playbook.
