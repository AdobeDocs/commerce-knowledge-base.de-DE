---
title: Wiederherstellen eines DB-Snapshots aus der Staging- oder Produktionsumgebung
description: Dieser Artikel zeigt, wie Sie einen DB-Snapshot aus der Staging- oder Produktionsumgebung in Adobe Commerce in der Cloud-Infrastruktur wiederherstellen.
exl-id: 1026a1c9-0ca0-4823-8c07-ec4ff532606a
source-git-commit: 193b5118342f380cef925766c0f7956a6592800c
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# Wiederherstellen eines DB-Snapshots aus [!DNL Staging] oder [!DNL Production]

Dieser Artikel zeigt, wie Sie eine DB-[!DNL snapshot] aus [!DNL Staging] oder [!DNL Production] in Adobe Commerce in der Cloud Pro-Infrastruktur wiederherstellen.


>[!NOTE]
>
>Mit diesen Methoden wird der **vollständige Snapshot“**.
>>Wenn Sie den Snapshot (**) wiederherstellen müssen** z. B. nur die Katalogtabellen wiederherstellen und dabei die Bestelltabellen intakt lassen, müssen Sie sich an Ihren Entwickler oder DBA wenden.


## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, [alle unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

Wählen Sie das für Ihren Fall am besten geeignete aus:

* [Methode 1: Übertragen Sie die  [!DNL dump]  auf Ihren lokalen Computer und importieren Sie sie](#meth2).
* [Methode 2: Importieren Sie die  [!DNL dump]  direkt vom Server](#meth3).

## Methode 1: Übertragen Sie die [!DNL dump] auf Ihren lokalen Computer und importieren Sie sie {#meth2}


>[!NOTE]
>
> Das Format des Schnappschusses bei **Azure-Projekten** ist unterschiedlich und enthält andere Datenbanken, die nicht importiert **können**.\
> Bevor Sie den Snapshot importieren, müssen Sie zusätzliche Schritte ausführen, um **die entsprechende Datenbank zu extrahieren** bevor Sie mit dem Dump-Import fortfahren.

Die Schritte sind:

1. Navigieren Sie mithilfe von [!DNL SFTP] zu dem Speicherort, an dem die [!DNL snapshot] platziert wurde, normalerweise auf dem ersten Server/Knoten Ihrer [!DNL cluster] (zum Beispiel: `/mnt/recovery-<recovery_id>`).
   > **Azure-basierte Projekte:**\
   > Wenn Ihr Projekt auf Azure basiert (d. h. Ihre Projekt-URL sieht wie `https://us-a1.magento.cloud/projects/<cluster_id>` aus), wird der Schnappschuss in folgendem Verzeichnis platziert:
   > * `/mnt/shared/<cluster ID>/all-databases.sql.gz`
   > * `/mnt/shared/<cluster ID_stg>/all-databases.sql.gz`

   **Azure-spezifische Extraktionsschritte**

   **Für die Produktion:**

   ```bash
   cd /mnt/shared/<cluster ID>/
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

   **Für das Staging:**

   ```bash
   cd /mnt/shared/<cluster ID_stg>/
   gunzip all-databases.sql.gz 
   head -n 17 all-databases.sql > <cluster ID_stg>.sql
   sed -n '/^-- Current Database: `<cluster ID_stg>`/,/^-- Current Database: `/p' all-databases.sql >> <cluster ID_stg>.sql 
   gzip <cluster ID_stg>.sql  
   zcat <cluster ID_stg>.sql.gz | \
   sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | \
   mysql -h 127.0.0.1 \
   -u $DB_USER \
   --password=$MYSQL_PWD $DB_NAME \
   --init-command="SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT ;SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS ;SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION ;SET NAMES utf8 ;SET @OLD_TIME_ZONE=@@TIME_ZONE ;SET TIME_ZONE='+00:00' ;SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 ;SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 ;SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' ;SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0;"
   ```

1. Kopieren Sie die [!DNL dump file] (z. B.: `<cluster ID>.sql.gz` für [!DNL Production] oder `<cluster ID_stg>.sql.gz` für [!DNL Staging]) auf Ihren lokalen Computer.
1. Stellen Sie sicher, dass Sie in unserer Entwicklerdokumentation die [!DNL SSH tunnel] eingerichtet haben, um eine Remote-Verbindung zur Datenbank herzustellen[[!DNL SSH]  „and [!DNL sFTP]: [!DNL SSH tunneling]](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections#env-start-tunn)&quot;.
1. Stellen Sie eine Verbindung zur Datenbank her.

   ```bash
   mysql -h <db-host> -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] der Datenbank; geben Sie bei der [!DNL MariaDB] ein:

   (für [!DNL Production])

   ```bash
   drop database <cluster ID>;
   ```

   (für [!DNL Staging])

   ```bash
   drop database <cluster ID_stg>;
   ```

1. Geben Sie den folgenden Befehl ein, um die [!DNL snapshot] zu importieren:

   (für [!DNL Production])

   ```bash
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

   (für [!DNL Staging])

   ```bash
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

## Methode 2: Importieren des Datenbank-[!DNL dump] direkt vom Server {#meth3}

Die Schritte sind:

1. Navigieren Sie zu dem Speicherort, an dem die [!DNL snapshot] platziert wurde, normalerweise auf dem ersten Server/Knoten Ihrer [!DNL cluster] (zum Beispiel: `/mnt/recovery-<recovery_id>`).
1. Um die Cloud-Datenbank zu [!DNL drop] und neu zu erstellen, stellen Sie zunächst eine Verbindung zur -Datenbank her:

   ```bash
   mysql -h 127.0.0.1 -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] der Datenbank; geben Sie bei der [!DNL MariaDB] ein:

   (für [!DNL Production])

   ```bash
   drop database <cluster ID>;
   ```

   (für [!DNL Staging])

   ```bash
   drop database <cluster ID_stg>;
   ```

1. Erstellen Sie die Datenbank nach dem Ablegen neu:

   ```bash
   create database [database_name];
   ```

1. Geben Sie den folgenden Befehl ein, um die [!DNL snapshot] zu importieren:

   (Zum Importieren der Datenbanksicherung aus [!DNL Production])

   ```bash
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (Zum Importieren der Datenbanksicherung aus [!DNL Staging])

   ```bash
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (Zum Importieren einer Datenbanksicherung aus einer beliebigen anderen Umgebung)

   ```bash
   zcat <database-backup-name>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (Zum Importieren einer Datenbanksicherung aus einer beliebigen anderen Umgebung)

   ```bash
   zcat <database-backup-name>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

## Verwandtes Lesen

In unserer Entwicklerdokumentation:

* [Importcode: Importieren Sie die Datenbank](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production)
* [[!DNL Snapshots] AND [!DNL backup] MANAGEMENT: [!DNL Dump] Ihre Datenbank](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots)
* [Backup (Snapshot) in Cloud: Häufig gestellte Fragen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/faq/backup-snapshot-on-cloud-faq)
