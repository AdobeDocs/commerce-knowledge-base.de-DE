---
title: Numerischer Adobe Commerce-Datenbankwert außerhalb des Bereichs, „INT“ bis „BIGINT“
description: Dieser Artikel bietet Lösungen für Fälle, in denen Sie eine Produktaktualisierung nicht speichern können, z. B. eine Preisänderung oder das Löschen und Duplizieren eines Produkts.
exl-id: e2a00371-9032-4e81-b60e-5456ba35be94
feature: Services
role: Developer
source-git-commit: 5ca7a4400e62db2419b32a31a4f6cf04f5a82e35
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 0%

---

# Numerischer Adobe Commerce-Datenbankwert außerhalb des Bereichs, `INT` bis `BIGINT`

>[!WARNING]
>
>Vor der Implementierung der Lösung in diesem Artikel (`INT` zur Aktualisierung `BIGINT` Schemas) müssen Händler immer überprüfen, ob das Feld, das sie ändern werden, KEINE Fremdschlüsselbeziehungen zu einer anderen Tabelle aufweist. Wenn das Feld Fremdschlüsselbeziehungen zu einer anderen Tabelle hat, treten Probleme auf, da das zugehörige Feld weiterhin `INT` ist. Sie können die folgende Abfrage verwenden, um dies zu überprüfen. Diese Abfrage listet die Fremdschlüsselbeziehungen auf, die in der Datenbank für das angegebene Tabellenfeld verfügbar sind:
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

* Adobe Commerce (alle Bereitstellungsmethoden) - alle [unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

Dieser Artikel bietet Lösungen für Fälle, in denen Sie eine Produktaktualisierung nicht speichern können, z. B. eine Preisänderung oder das Löschen und Duplizieren eines Produkts.
Möglicherweise wird die Fehlermeldung angezeigt *Das Lagerelement konnte nicht gespeichert werden. Bitte erneut versuchen.* Die Bereitstellung kann nach einer Produktaktualisierung fehlschlagen. Möglicherweise wird auch die folgende [!DNL MySQL]-Fehlermeldung beim Ausführen von `php bin/magento setup:upgrade` angezeigt (in Adobe Commerce in der Cloud-Infrastruktur wird dieser Fehler in den Bereitstellungsprotokollen angezeigt):

```mysql
SQLSTATE[22003]: Numeric value out of range: 167 Out of range value for column 'value_id' at row 1, query was: INSERT INTO `catalog_product_entity_decimal` (`attribute_id`,`store_id`,`row_id`,`value`) VALUES (?, ?, ?, ?) ON DUPLICATE KEY UPDATE `attribute_id` = VALUES(`attribute_id`), `store_id` = VALUES(`store_id`), `row_id` = VALUES(`row_id`), `value` = VALUES(`value`)
```

Die im Artikel beschriebenen Lösungen sind:
* Aktualisieren Sie die `[ AUTO_INCREMENT ]` auf den nächsten Wert aus der Tabelle oder
* Aktualisierung des `INT`-Schemas `BIGINT`

Welche Lösung Sie verwenden, hängt von der Ursache des Problems ab. Gehen Sie wie folgt vor, um die Ursache zu isolieren.

## Schritte zur Prüfung der Ursache


Überprüfen Sie den höchsten Wert des Primärschlüssels, indem Sie den folgenden Befehl am Terminal ausführen: `SELECT MAX(value_id) FROM catalog_product_entity_int;`

Wenn der `max(value_id)` kleiner als der `max int(11) [ 4294967296 ]` ist und der `[ AUTO_INCREMENT ]` einen Wert größer oder gleich dem `max int(11) [ 4294967296 ]` hat, [ Sie (den `[ AUTO_INCREMENT ]` auf den nächsten Wert aus der Tabelle aktualisieren](#update-the-auto-increment-to-the-next-value-from-the-table). Andernfalls sollten Sie eine [`INT` zur Aktualisierung `BIGINT` Schemas ](#int_to_bigint_schema_update).

## Aktualisieren Sie die `AUTO_INCREMENT` auf den nächsten Wert aus der Tabelle. {#update-the-auto-increment-to-the-next-value-from-the-table}

>[!WARNING]
>
>Führen Sie eine Datenbanksicherung durch, bevor Sie die Tabellen ändern. Setzen Sie die Site auch in den [Wartungsmodus](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#maintenance-mode). Darüber hinaus wird empfohlen, den Befehl [!DNL MySQL] optimieren für die Datenbanktabellen (nur für Tabellen, in denen Änderungen vorgenommen wurden) auszuführen, nachdem die Änderungen vorgenommen wurden.

>[!NOTE]
>
>Die Site sollte sich im Wartungsmodus befinden, während der Befehl „optimieren“ für bestimmte Tabellen ausgeführt wird. Dadurch werden Tabellen vollständig neu erstellt und nach dem Löschen von Daten aus Tabellen Speicherplatz freigegeben.

Wenn der angezeigte Wert kleiner als `max int(11) [ 4294967296 ]` ist, wie in der folgenden Beispiel-Terminalausgabe gezeigt, dann hat sich eine `[ AUTO_INCREMENT ]` in eine Zahl geändert, die größer oder gleich dem `max [ int(11) ]` ist.

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

Wie Sie in der obigen Beispielausgabe sehen können, hat sich die Tabelle `[ AUTO_INCREMENT ]` in eine größere Zahl geändert als die `max int(11) [ 4294967296 ]`. Die Lösung besteht darin, die `[ AUTO_INCREMENT]` auf den nächsten Wert aus der Tabelle zu aktualisieren:

```
ALTER TABLE catalog_product_entity_int AUTO_INCREMENT = 4283174131;
```

## Aktualisierung des `INT`-Schemas `BIGINT` {#int_to_bigint_schema_update}

Wenn jedoch beim Ausführen der folgenden Abfrage `SELECT MAX(value_id) FROM catalog_product_entity_int;` der angezeigte Wert höher ist als `max int(11) [ 4294967296 ]` eine `INT` zur `BIGINT` Schemaaktualisierung in Betracht ziehen. Der Datentyp `BIGINT` hat einen größeren Wertebereich.

Gehen Sie dazu folgendermaßen vor:

1. Erstellen Sie ein benutzerdefiniertes Modul im Verzeichnis *app/code/*.
1. Erstellen Sie im benutzerdefinierten Modul eine Datei *db_schema.xml*. In *db_schema.xml* Sie den Datentyp auf `BIGINT` festlegen.
1. Fügen Sie den folgenden Inhalt hinzu und führen Sie dann `bin/magento setup:upgrade` aus, um die oben genannten Änderungen auf die entsprechende Tabelle anzuwenden.

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

* [Allgemein [!DNL MySQL] Richtlinien](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql.html) im Commerce-Installationshandbuch
* [Best Practices für Datenbanken für Adobe Commerce auf Cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/database-best-practices-for-magento-commerce-cloud.html)Infrastruktur in unserer Support-Wissensdatenbank
* [Häufigste Datenbankprobleme in Adobe Commerce auf Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/most-common-database-issues-in-magento-commerce-cloud.html) in unserer Support-Wissensdatenbank
* [Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook
