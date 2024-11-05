---
title: Numerischer Wert der Adobe Commerce-Datenbank außerhalb des Bereichs, "INT"bis "BIGINT"
description: Dieser Artikel bietet Lösungen für Fälle, in denen Sie eine Produktaktualisierung nicht speichern können, z. B. eine Preisänderung oder das Löschen und Duplizieren eines Produkts.
exl-id: e2a00371-9032-4e81-b60e-5456ba35be94
feature: Services
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 0%

---

# Numerischer Wert der Adobe Commerce-Datenbank außerhalb des Bereichs, `INT` bis `BIGINT`

>[!WARNING]
>
>Vor der Implementierung der Lösung in diesem Artikel (`INT` in `BIGINT` Schema-Update) müssen Händler immer überprüfen, ob das Feld, das sie ändern werden, KEINE Fremdschlüsselbeziehungen zu einer anderen Tabelle aufweist. Wenn das Feld Beziehungen mit Fremdschlüsseln zu einer anderen Tabelle aufweist, treten Probleme auf, da das zugehörige Feld immer noch `INT` ist. Sie können die folgende Abfrage verwenden, um dies zu überprüfen. Diese Abfrage listet die Fremdschlüsselbeziehungen auf, die in der Datenbank für das angegebene Tabellenfeld verfügbar sind:
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

* Adobe Commerce (alle Bereitstellungsmethoden) alle [unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

Dieser Artikel bietet Lösungen für Fälle, in denen Sie eine Produktaktualisierung nicht speichern können, z. B. eine Preisänderung oder das Löschen und Duplizieren eines Produkts.
Möglicherweise wird die Fehlermeldung *Das Lagerelement konnte nicht gespeichert werden. Bitte versuchen Sie es erneut.* Nach einer Produktaktualisierung können Sie möglicherweise nicht bereitstellen. Möglicherweise wird auch die folgende [!DNL MySQL] -Fehlermeldung angezeigt, wenn Sie `php bin/magento setup:upgrade` ausführen (in Adobe Commerce in der Cloud-Infrastruktur wird dieser Fehler in den Bereitstellungsprotokollen angezeigt):

```mysql
SQLSTATE[22003]: Numeric value out of range: 167 Out of range value for column 'value_id' at row 1, query was: INSERT INTO `catalog_product_entity_decimal` (`attribute_id`,`store_id`,`row_id`,`value`) VALUES (?, ?, ?, ?) ON DUPLICATE KEY UPDATE `attribute_id` = VALUES(`attribute_id`), `store_id` = VALUES(`store_id`), `row_id` = VALUES(`row_id`), `value` = VALUES(`value`)
```

Die im Artikel beschriebenen Lösungen sind:
* Aktualisieren Sie die `[ AUTO_INCREMENT ]` auf den nächsten Wert aus der Tabelle oder
* Schemaaktualisierung `INT` bis `BIGINT`

Welche Lösung Sie verwenden, hängt von der Ursache des Problems ab. Gehen Sie wie folgt vor, um die Ursache zu isolieren.

## Schritte zum Überprüfen der Ursache


Überprüfen Sie den höchsten Wert des Primärschlüssels, indem Sie den folgenden Befehl im Terminal ausführen: `SELECT MAX(value_id) FROM catalog_product_entity_int;`

Wenn der `max(value_id)` kleiner als der `max int(11) [ 4294967296 ]` ist und der `[ AUTO_INCREMENT ]` einen Wert größer oder gleich dem `max int(11) [ 4294967296 ]` hat, sollten Sie in Erwägung ziehen, [die `[ AUTO_INCREMENT ]` auf den nächsten Wert aus der Tabelle](#update-the-auto-increment-to-the-next-value-from-the-table) zu aktualisieren. Ansonsten sollten Sie ein [`INT` - `BIGINT` Schema-Update](#int_to_bigint_schema_update) in Erwägung ziehen.

## Aktualisieren Sie den `AUTO_INCREMENT` auf den nächsten Wert aus der Tabelle {#update-the-auto-increment-to-the-next-value-from-the-table}

>[!WARNING]
>
>Führen Sie vor dem Ändern der Tabellen eine Datenbanksicherung durch. Versetzen Sie die Site außerdem in den [Wartungsmodus](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#maintenance-mode). Darüber hinaus wird empfohlen, den Befehl [!DNL MySQL] optimize nach Durchführung der Änderungen in den Datenbanktabellen auszuführen (nur in Tabellen, in denen Änderungen vorgenommen wurden).

>[!NOTE]
>
>Die Site sollte sich im Wartungsmodus befinden, während der Optimierungsbefehl für bestimmte Tabellen ausgeführt wird. Dadurch werden Tabellen vollständig neu erstellt und nach dem Löschen von Daten aus Tabellen wird Speicherplatz freigesetzt.

Wenn der angezeigte Wert kleiner als `max int(11) [ 4294967296 ]` ist, wie im folgenden Beispiel für die Terminal-Ausgabe gezeigt, hat sich eine Tabelle `[ AUTO_INCREMENT ]` in eine Zahl geändert, die größer oder gleich dem `max [ int(11) ]` -Wert ist.

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

Wie Sie in der obigen Beispielausgabe sehen können, hat sich die Tabelle `[ AUTO_INCREMENT ]` in eine größere Zahl als die `max int(11) [ 4294967296 ]` geändert. Die Lösung besteht darin, den `[ AUTO_INCREMENT]` auf den nächsten Wert aus der Tabelle zu aktualisieren:

```
ALTER TABLE catalog_product_entity_int AUTO_INCREMENT = 4283174131;
```

## Schemaaktualisierung `INT` bis `BIGINT` {#int_to_bigint_schema_update}

Wenn jedoch bei Ausführung der folgenden Abfrage `SELECT MAX(value_id) FROM catalog_product_entity_int;` der angezeigte Wert höher als `max int(11) [ 4294967296 ]` ist, sollten Sie eine Schemaaktualisierung vom Typ `INT` bis `BIGINT` vornehmen. Der Datentyp `BIGINT` hat einen größeren Wertebereich.

Gehen Sie dazu folgendermaßen vor:

1. Erstellen Sie ein benutzerdefiniertes Modul im Ordner *app/code/* .
1. Erstellen Sie im benutzerdefinierten Modul eine *db_schema.xml* -Datei. In *db_schema.xml* legen Sie den Datentyp auf `BIGINT` fest.
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

* [Allgemein [!DNL MySQL] richtlinien](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql.html) im Commerce-Installationshandbuch
* [Der Upload der Datenbank verliert die Verbindung zu  [!DNL MySQL]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/database-upload-loses-connection-to-mysql.html) in unserer Wissensdatenbank für die Unterstützung
* [Best Practices für die Datenbank für Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/database-best-practices-for-magento-commerce-cloud.html) in unserer Support-Wissensdatenbank
* [ Die häufigsten Datenbankprobleme in Adobe Commerce bei der Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/most-common-database-issues-in-magento-commerce-cloud.html) in unserer Support-Wissensdatenbank
* [Best Practices für die Änderung von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Playbook für die Commerce-Implementierung
