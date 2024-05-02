---
title: Wiederherstellen eines DB-Schnappschusses aus Staging oder Produktion
description: Dieser Artikel zeigt, wie Sie einen DB-Schnappschuss aus Staging oder Produktion in Adobe Commerce in der Cloud-Infrastruktur wiederherstellen können.
exl-id: 1026a1c9-0ca0-4823-8c07-ec4ff532606a
source-git-commit: b9e72ff8d541ad01788e5198e03abcb46a1bd11f
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# Wiederherstellen eines DB-Snapshots aus [!DNL Staging] oder [!DNL Production]

Dieser Artikel zeigt, wie eine DB wiederhergestellt wird [!DNL snapshot] von [!DNL Staging] oder [!DNL Production] auf der Adobe Commerce on Cloud Pro-Infrastruktur.

## Betroffene Produkte und Versionen

* Adobe Commerce zur Cloud-Infrastruktur, [alle unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

Wählen Sie die für Ihren Fall am besten geeignete Option aus:

* [Methode 1: Datenbank übertragen [!DNL dump] auf Ihren lokalen Computer laden und importieren](#meth2).
* [Methode 2: Import der Datenbank [!DNL dump] direkt vom Server](#meth3).

## Methode 1: Datenbank übertragen [!DNL dump] auf Ihren lokalen Computer laden und importieren {#meth2}

Die Schritte sind:

1. Verwenden [!DNL sFTP], navigieren Sie zum Speicherort der Datenbank. [!DNL snapshot] wurde platziert, normalerweise auf dem ersten Server/Knoten Ihrer [!DNL cluster] (Beispiel: `/mnt/recovery-<recovery_id>`). HINWEIS: Wenn Ihr Projekt Azure-basiert ist, d. h. Ihre Projekt-URL sieht ungefähr wie https://us-a1.magento.cloud/projects/ aus.&lt;cluster_id>, wird der Schnappschuss in `/mnt/shared/<cluster ID>/all-databases.sql.gz` oder `/mnt/shared/<cluster ID_stg>/all-databases.sql.gz` anstatt.

   HINWEIS: Das Format der Momentaufnahme bei Azure-Projekten ist anders und enthält andere Datenbanken, die nicht importiert werden können. Vor dem Import des Snapshots müssen Sie zusätzliche Schritte unternehmen, um die entsprechende Datenbank zu extrahieren, bevor Sie den Dump importieren.

   Für die Produktion:

   ```sql
   cd /mnt/shared/<cluster ID/
   gunzip all-databases.sql.gz 
   head -n 17 all-databases.sql > <cluster ID>.sql 
   sed -n '/^-- Current Database: `<cluster ID>`/,/^-- Current Database: `/p' all-databases.sql >> <cluster ID>.sql gzip <cluster ID>.sql
   zcat <cluster ID>.sql.gz | \
   sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | \
   mysql -h 127.0.0.1 \
   -u $DB_USER \
   --password=$MYSQL_PWD $DB_NAME \
   --init-command="SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT ;SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS ;SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION ;SET NAMES utf8 ;SET @OLD_TIME_ZONE=@@TIME_ZONE ;SET TIME_ZONE='+00:00' ;SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 ;SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 ;SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' ;SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0;"
   ```

   Für das Staging:

   ```sql
   cd /mnt/shared/<cluster ID/ | cd /mnt/shared/<cluster ID_stg>
   gunzip all-databases.sql.gz 
   head -n 17 all-databases.sql > <cluster ID_stg>.sql
   sed -n '/^-- Current Database: `wyf2o4zlrljjs`/,/^-- Current Database: `/p' all-databases.sql >> <cluster ID_stg>.sql 
   gzip <cluster ID_stg>.sql  
   zcat <cluster ID_stg>.sql.gz | \
   sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | \
   mysql -h 127.0.0.1 \
   -u $DB_USER \
   --password=$MYSQL_PWD $DB_NAME \
   --init-command="SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT ;SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS ;SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION ;SET NAMES utf8 ;SET @OLD_TIME_ZONE=@@TIME_ZONE ;SET TIME_ZONE='+00:00' ;SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 ;SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 ;SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' ;SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0;"
   ```

1. Datenbank kopieren [!DNL dump file] (Beispiel: `<cluster ID>.sql.gz` für [!DNL Production] oder `<cluster ID_stg>.sql.gz` für [!DNL Staging]) auf Ihren lokalen Computer.
1. Stellen Sie sicher, dass Sie die [!DNL SSH tunnel] zur Remote-Verbindung mit der Datenbank: [[!DNL SSH] und [!DNL sFTP]: [!DNL SSH tunneling]](https://devdocs.magento.com/cloud/env/environments-ssh.html#env-start-tunn) in unserer Entwicklerdokumentation.
1. Stellen Sie eine Verbindung zur Datenbank her.

   ```sql
   mysql -h <db-host> -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] Datenbank, [!DNL MariaDB] Eingabeaufforderung, geben Sie ein:

   (Für [!DNL Production])

   ```sql
   drop database <cluster ID>;
   ```

   (Für [!DNL Staging])

   ```sql
   drop database <cluster ID_stg>;
   ```

1. Geben Sie den folgenden Befehl ein, um die [!DNL snapshot]:

   (Für [!DNL Production])

   ```sql
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

   (Für [!DNL Staging])

   ```sql
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

## Methode 2: Import der Datenbank [!DNL dump] direkt vom Server {#meth3}

Die Schritte sind:

1. Navigieren Sie zum Speicherort der Datenbank. [!DNL snapshot] wurde platziert, normalerweise auf dem ersten Server/Knoten Ihrer [!DNL cluster] (Beispiel: `/mnt/recovery-<recovery_id>`).
1. nach [!DNL drop] und erstellen Sie die Cloud-Datenbank neu, verbinden Sie sich zunächst mit der Datenbank:

   ```sql
   mysql -h 127.0.0.1 -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] Datenbank, [!DNL MariaDB] Eingabeaufforderung, geben Sie ein:

   (Für [!DNL Production])

   ```sql
   drop database <cluster ID>;
   ```

   (Für [!DNL Staging])

   ```sql
   drop database <cluster ID_stg>;
   ```

1. Geben Sie den folgenden Befehl ein, um die [!DNL snapshot]:

   (Für [!DNL Production])

   ```sql
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (Für [!DNL Staging])

   ```sql
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

## Verwandtes Lesen

In unserer Entwicklerdokumentation:

* [Import-Code: Import der Datenbank](https://devdocs.magento.com/cloud/setup/first-time-setup-import-import.html#cloud-import-db)
* [[!DNL Snapshots] und [!DNL backup] Management: [!DNL Dump] Ihre Datenbank](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump)
