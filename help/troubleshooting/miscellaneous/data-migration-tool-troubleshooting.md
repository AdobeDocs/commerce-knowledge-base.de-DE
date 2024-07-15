---
title: Fehlerbehebung beim Datenmigrationswerkzeug
description: Dieser Artikel enthält Lösungen für Fehler, die beim Ausführen des Datenmigrationswerkzeugs auftreten können.
exl-id: 9beb31ae-ed3c-42e1-b0bf-33fb1c91e0ea
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---

# Fehlerbehebung beim Datenmigrationswerkzeug

Dieser Artikel enthält Lösungen für Fehler, die beim Ausführen des Datenmigrationswerkzeugs auftreten können.

## Nicht zugeordnete Source-Dokumente/Felder {#source-documents-fields-not-mapped}

### Fehlermeldungen

* ```bash    Source documents are not mapped: <EXTENSION_TABLE>    ```
* ```bash    Source fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <EXTENSION_FIELD>    ```

In seltenen Fällen kann die Nachricht

```bash
Destination documents
```

oder

```bash
Destination fields
```

anstelle von Quellcodes.

### Ursache

Einige Entitäten der Adobe Commerce-Version 1 (in den meisten Fällen von Erweiterungen) sind nicht in der Adobe Commerce-Datenbank Version 2 enthalten.

Diese Meldung wird angezeigt, weil das Datenmigrationswerkzeug interne Tests durchführt, um sicherzustellen, dass Tabellen und Felder zwischen den Datenbanken *source* (Adobe Commerce 1) und *destination* (Adobe Commerce 2) konsistent sind.

### Mögliche Lösungen

* Installieren Sie die entsprechenden Adobe Commerce 2-Erweiterungen von [Commerce Marketplace](https://marketplace.magento.com/).     Wenn die in Konflikt stehenden Daten aus einer Erweiterung stammen, durch die eigene Datenbankstrukturelemente hinzugefügt werden, kann die Adobe Commerce 2-Version derselben Erweiterung solche Elemente zur Zieldatenbank (Adobe Commerce 2) hinzufügen, wodurch das Problem behoben wird.
* Verwenden Sie beim Ausführen des Tools das Argument `-a` , um Fehler automatisch zu beheben und zu verhindern, dass die Migration angehalten wird.
* Konfigurieren Sie das Tool, um die problematischen Daten zu ignorieren.

Um Datenbankentitäten zu ignorieren, fügen Sie das Tag `<ignore>` wie folgt zu einer Entität in der Datei `map.xml` hinzu:

```xml
...
    <source>
        <document_rules>
            ...
            <!-- Ignore `sales_flat_invoice_grid` table -->
            <ignore>
                <document>sales_flat_invoice_grid</document>
            </ignore>
            <!-- Ignore `address_id` field of `sales_flat_order_address` table -->
            <ignore>
                <field>sales_flat_order_address.address_id</field>
            </ignore>
            ...
        </document_rules>
    </source>
    ...
```

>[!WARNING]
>
>Bevor Sie Entitäten anhand der Zuordnungsdatei oder der Option `-a` ignorieren, stellen Sie sicher, dass Sie die betroffenen Daten nicht in Ihrem Adobe Commerce 2-Store benötigen.

## Die Klasse wird im Datensatz nicht zugeordnet {#class-does-not-exist-but-mentioned}

### Fehlermeldung

```bash
Class <extension/class_name> is not mapped in record <attribute_id=196>
```

### Ursache

Eine Klasse aus der Adobe Commerce 1-Codebase konnte während des [EAV-Migrationsschritts](https://devdocs.magento.com/guides/v2.3/migration/migration-tool-internal-spec.html#eav) in unserer Entwicklerdokumentation nicht in der Adobe Commerce 2-Codebase gefunden werden. In den meisten Fällen gehört die fehlende Klasse zu einer [Erweiterung](https://glossary.magento.com/extension).

### Mögliche Lösungen

* Installieren Sie die entsprechende Adobe Commerce 2-Erweiterung.
* Ignorieren Sie das Attribut, das das Problem verursacht.    Fügen Sie dazu das Attribut der Gruppe `ignore` in der Datei `eav-attribute-groups.xml.dist` hinzu.
* Fügen Sie die Klassenzuordnung mithilfe der Datei `class-map.xml.dist` hinzu.

## Fremdschlüsseleinschränkung schlägt fehl

### Text der Fehlermeldung

```bash
Foreign key <KEY_NAME> constraint fails on source database. Orphan records id: <id_1>, <id_2> from <child_table>.<field_id> has no referenced records in <parent_table>
```

### Ursache

Es fehlen Datenbankdatensätze in der `parent_table`, auf die die `field_id` der `child_table` verweisen.

### Lösung

Löschen Sie die Datensätze aus dem `child_table` , wenn Sie sie nicht benötigen.

Um die Datensätze beizubehalten, deaktivieren Sie die `Data Integrity Step` , indem Sie die `config.xml` des Datenmigrationswerkzeugs ändern.

## Duplikate in URL-Neuschreibungen

```xml
There are duplicates in URL rewrites:
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/10
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/12
```

### Ursache

Die `Target path` in einer URL-Neuschreibungsoption muss durch ein eindeutiges Paar aus `Request path` + `Store ID` angegeben werden. Dieser Fehler meldet zwei Einträge, die dasselbe `Request path` + `Store ID`-Paar mit zwei verschiedenen `Target path` -Werten verwenden.

### Lösung

Aktivieren Sie die Option `auto_resolve_urlrewrite_duplicates` in Ihrer `config.xml` -Datei.

Diese Konfiguration fügt den in Konflikt stehenden Datensätzen von [URL](https://glossary.magento.com/url) eine Hash-Zeichenfolge hinzu und zeigt das Auflösungsergebnis in Ihrer Befehlszeilenschnittstelle an.

## Unstimmigkeiten zwischen Entitäten {#mismatch-of-entities}

### Fehlermeldung

```bash
Mismatch of entities in the document: <DOCUMENT> Source: <COUNT_ITEMS_IN_SOURCE_TABLE> Destination: <COUNT_ITEMS_IN_DESTINATION_TABLE>
```

### Ursache

Der Fehler tritt während der Lautstärkeprüfung auf. Das bedeutet, dass die Datensatzanzahl der Adobe Commerce 2-Datenbank des Dokuments nicht mit der in Adobe Commerce 1 übereinstimmt.

Fehlende Datensätze treten auf, wenn ein Kunde während der Migration eine Bestellung aufgibt.

### Lösung

Führen Sie das Datenmigrationswerkzeug im Modus `Delta` aus, um inkrementelle Änderungen zu übertragen.

## Deltalog ist nicht installiert {#deltalog-is-not-installed}

### Fehlermeldung

```bash
Deltalog for <TABLE_NAME> is not installed
```

### Ursache

Dieser Fehler tritt während der [inkrementellen Migration](https://devdocs.magento.com/guides/v2.3/migration/migration-migrate-delta.html) (in unserer Entwicklerdokumentation) von Datenänderungen auf. Dies bedeutet, dass Deltalog-Tabellen (mit dem Präfix &quot;`m2_cl_*`&quot;) nicht in der Adobe Commerce 1-Datenbank gefunden wurden. Das Tool installiert diese Tabellen während der [Datenmigration](https://devdocs.magento.com/guides/v2.3/migration/migration-migrate-data.html) (in unserer Entwicklerdokumentation) sowie Datenbank-Trigger, die Änderungen verfolgen und Löschtabellen ausfüllen.

Ein Grund für den Fehler könnte sein, dass Sie versuchen, eine Migration von einem *copy* Ihres Live-Adobe Commerce 1-Stores durchzuführen und nicht vom Live Store selbst. Wenn Sie eine Kopie aus einem Live-Adobe Commerce 1-Store erstellen, der noch nie migriert wurde, enthält die Kopie nicht die Trigger und zusätzlichen Deltalog-Tabellen, die zum Abschließen einer Delta-Migration erforderlich sind. Daher schlägt die Migration fehl. Das Datenmigrationswerkzeug führt KEINE Vergleiche zwischen der DB von AC1 und AC2 durch, um die Unterschiede zu migrieren. Stattdessen verwendet das Tool die während der ersten Migration installierten Trigger und Deltalog-Tabellen, um nachfolgende Deltammigationen durchzuführen. In diesem Fall enthält Ihre Kopie der Live-Adobe Commerce 1-DB nicht die Trigger und Deltalog-Tabellen, die das Datenmigrationswerkzeug zum Ausführen einer Migration verwendet.

### Lösung

Wir empfehlen, den Migrationsprozess von einer Kopie Ihrer Adobe Commerce 1-Datenbank zu testen, um Ihre Migrationsprobleme zu beheben. Nachdem Sie die Probleme in der Kopie behoben haben, starten Sie den Migrationsprozess von Ihrer Live-Adobe Commerce 1-Datenbank aus erneut. Dies wird zu einem reibungslosen Migrationsprozess beitragen.
