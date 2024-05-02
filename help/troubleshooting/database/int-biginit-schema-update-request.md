---
title: Numerischer Wert der Adobe Commerce-Datenbank außerhalb des Bereichs, "INT"bis "BIGINT"
description: Dieser Artikel bietet Lösungen für Fälle, in denen Sie eine Produktaktualisierung nicht speichern können, z. B. eine Preisänderung oder das Löschen und Duplizieren eines Produkts.
exl-id: e2a00371-9032-4e81-b60e-5456ba35be94
feature: Services
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# Numerischer Wert der Adobe Commerce-Datenbank außerhalb des Bereichs, `INT` nach `BIGINT`

>[!WARNING]
>
>Vor der Implementierung der Lösung in diesem Artikel (`INT` nach `BIGINT` Schemaaktualisierung) müssen Händler stets sicherstellen, dass das Feld, das sie ändern werden, KEINE Fremdschlüsselbeziehungen zu einer anderen Tabelle aufweist. Wenn das Feld Beziehungen mit Fremdschlüsseln zu einer anderen Tabelle aufweist, treten Probleme auf, da das zugehörige Feld weiterhin `INT`. Sie können die folgende Abfrage verwenden, um dies zu überprüfen. Diese Abfrage listet die Fremdschlüsselbeziehungen auf, die in der Datenbank für das angegebene Tabellenfeld verfügbar sind:
>
```mysql
>SELECT 
>     TABLE_NAME,COLUMN_NAME,CONSTRAINT_NAME,REFERENCED_TABLE_NAME,REFERENCED_COLUMN_NAME
>FROM
>   INFORMATION_SCHEMA.KEY_COLUMN_USAGE
>WHERE
>     REFERENCED_TABLE_SCHEMA = '<database_name>' AND
>     REFERENCED_TABLE_NAME = '<table_name>' AND
>     REFERENCED_COLUMN_NAME = '<table_field>';
>```

## Betroffene Produkte und Versionen

* Adobe Commerce (alle Bereitstellungsmethoden) alle [unterstützte Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

Dieser Artikel bietet Lösungen für Fälle, in denen Sie eine Produktaktualisierung nicht speichern können, z. B. eine Preisänderung oder das Löschen und Duplizieren eines Produkts.
Möglicherweise wird die Fehlermeldung angezeigt. *Der Lagerbestand konnte nicht gespeichert werden. Bitte versuchen Sie es erneut.* Nach einer Produktaktualisierung kann es sein, dass die Bereitstellung fehlschlägt. Möglicherweise wird auch die folgende MySQL-Fehlermeldung angezeigt, wenn Sie `php bin/magento setup:upgrade` (In Adobe Commerce zur Cloud-Infrastruktur wird dieser Fehler in den Bereitstellungsprotokollen angezeigt):

```mysql
SQLSTATE[22003]: Numeric value out of range: 167 Out of range value for column 'value_id' at row 1, query was: INSERT INTO `catalog_product_entity_decimal` (`attribute_id`,`store_id`,`row_id`,`value`) VALUES (?, ?, ?, ?) ON DUPLICATE KEY UPDATE `attribute_id` = VALUES(`attribute_id`), `store_id` = VALUES(`store_id`), `row_id` = VALUES(`row_id`), `value` = VALUES(`value`)
```

Die im Artikel beschriebenen Lösungen sind:
* Aktualisieren Sie die `[ AUTO_INCREMENT ]` zum nächsten Wert aus der Tabelle oder
* `INT` nach `BIGINT` Schemaaktualisierung

Welche Lösung Sie verwenden, hängt von der Ursache des Problems ab. Gehen Sie wie folgt vor, um die Ursache zu isolieren.

## Schritte zum Überprüfen der Ursache


Überprüfen Sie den höchsten Wert des Primärschlüssels, indem Sie den folgenden Befehl im Terminal ausführen: `SELECT MAX(value_id) FROM catalog_product_entity_int;`

Wenn die Variable `max(value_id)` kleiner als der Wert `max int(11) [ 4294967296 ]`und die `[ AUTO_INCREMENT ]` einen Wert hat, der größer oder gleich der `max int(11) [ 4294967296 ]`, dann sollten Sie [aktualisieren `[ AUTO_INCREMENT ]` zum nächsten Wert aus der Tabelle](#update-the-auto-increment-to-the-next-value-from-the-table). Ansonsten sollten Sie eine [`INT` nach `BIGINT` Schemaaktualisierung](#int_to_bigint_schema_update).

## Aktualisieren Sie die `AUTO_INCREMENT` zum nächsten Wert aus der Tabelle {#update-the-auto-increment-to-the-next-value-from-the-table}

>[!WARNING]
>
>Führen Sie vor dem Ändern der Tabellen eine Datenbanksicherung durch. Fügen Sie außerdem die Site in [Wartungsmodus](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#maintenance-mode). Darüber hinaus wird empfohlen, den MYSQL-Optimierungsbefehl für die Datenbanktabellen (nur für Tabellen, in denen Änderungen vorgenommen wurden) auszuführen, nachdem die Änderungen vorgenommen wurden.

>[!NOTE]
>
>Die Site sollte sich im Wartungsmodus befinden, während der Optimierungsbefehl für bestimmte Tabellen ausgeführt wird. Dadurch werden Tabellen vollständig neu erstellt und nach dem Löschen von Daten aus Tabellen wird Speicherplatz freigesetzt.

Wenn der angezeigte Wert kleiner ist als `max int(11) [ 4294967296 ]` wie in der folgenden Beispiel-Terminal-Ausgabe gezeigt, anstatt einer Tabelle `[ AUTO_INCREMENT ]` hat sich in eine Zahl geändert, die größer oder gleich der `max [ int(11) ]` -Wert.

```mariadb
MariaDB [xxx]> SELECT MAX(value_id) FROM catalog_product_entity_int;
+---------------------+
| MAX(source_item_id) |
+---------------------+
|          4283174130 |
+---------------------+
```

Um zu überprüfen, ob dies geschehen ist, führen Sie den folgenden Befehl im Terminal aus:

```
MariaDB [xxx]> show create table catalog_product_entity_int;

...
) ENGINE=InnoDB AUTO_INCREMENT=4294967297 DEFAULT CHARSET=utf8 COMMENT='Catalog Product Integer Attribute Backend Table';
```

Wie Sie im obigen Beispiel sehen können, wird die Tabelle ausgegeben `[ AUTO_INCREMENT ]` hat sich in eine größere Zahl geändert als die `max int(11) [ 4294967296 ]`. Die Lösung besteht darin, die `[ AUTO_INCREMENT]` zum nächsten Wert aus der Tabelle:

```
ALTER TABLE catalog_product_entity_int AUTO_INCREMENT = 4283174131;
```

## `INT` nach `BIGINT` Schemaaktualisierung {#int_to_bigint_schema_update}

Wenn jedoch beim Ausführen der folgenden Abfrage `SELECT MAX(value_id) FROM catalog_product_entity_int;` der angezeigte Wert höher ist als `max int(11) [ 4294967296 ]`  erwägen, `INT` nach `BIGINT` Schemaaktualisierung. Der Datentyp `BIGINT` hat einen größeren Wertebereich.

Gehen Sie dazu folgendermaßen vor:

1. Erstellen Sie ein benutzerdefiniertes Modul im *app/code/* Verzeichnis.
1. Erstellen Sie im benutzerdefinierten Modul eine *db_schema.xml*. In *db_schema.xml* setzen Sie den Datentyp auf `BIGINT`.
1. Fügen Sie den folgenden Inhalt hinzu und führen Sie dann `bin/magento setup:upgrade` , um die oben genannten Änderungen auf die entsprechende Tabelle anzuwenden.

```
<?xml version="1.0"?>
<schema xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Setup/Declaration/Schema/etc/schema.xsd">
    <table name="catalog_product_entity_int">
        <column xsi:type="bigint" name="value_id" unsigned="false" nullable="false" identity="true"
                comment="Value ID"/>
    </table>
</schema>
```


## Verwandtes Lesen

* [Allgemeine MySQL-Richtlinien](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql.html) im Commerce-Installationshandbuch.
* [Beim Hochladen der Datenbank wird die Verbindung zu MySQL unterbrochen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/database-upload-loses-connection-to-mysql.html) in unserer Wissensdatenbank.
* [Best Practices für Datenbanken mit Adobe Commerce in Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/database-best-practices-for-magento-commerce-cloud.html) in unserer Wissensdatenbank.
* [Häufigste Datenbankprobleme in Adobe Commerce bei der Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/most-common-database-issues-in-magento-commerce-cloud.html) in unserer Wissensdatenbank.
