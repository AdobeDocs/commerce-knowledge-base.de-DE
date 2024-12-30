---
title: Fehlerbehebung beim Datenmigrations-Tool
description: Dieser Artikel enthält Lösungen für Fehler, die beim Ausführen des Datenmigrations-Tools auftreten können.
exl-id: 9beb31ae-ed3c-42e1-b0bf-33fb1c91e0ea
feature: Data Import/Export
role: Developer
source-git-commit: 958067830d32b1f10ffa669307ec76d1e14b82a4
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---

# Fehlerbehebung beim Datenmigrations-Tool

Dieser Artikel enthält Lösungen für Fehler, die beim Ausführen des Datenmigrations-Tools auftreten können.

## Source-Dokumente/-Felder nicht zugeordnet {#source-documents-fields-not-mapped}

### Fehlermeldungen

* ```bash    Source documents are not mapped: <EXTENSION_TABLE>    ```
* ```bash    Source fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <EXTENSION_FIELD>    ```

In seltenen Fällen wird in der Meldung Folgendes erwähnt

```bash
Destination documents
```

oder

```bash
Destination fields
```

anstelle von Quelltexten.

### Ursache

Einige Entitäten von Adobe Commerce Version 1 (in den meisten Fällen von Erweiterungen) sind nicht in der Adobe Commerce Version 2-Datenbank vorhanden.

Diese Meldung wird angezeigt, weil das Datenmigrations-Tool interne Tests ausführt, um zu überprüfen, ob Tabellen und Felder zwischen *Quelldatenbank* (Adobe Commerce 1) und *Zieldatenbank* (Adobe Commerce 2) konsistent sind.

### Mögliche Lösungen

* Installieren Sie die entsprechenden Adobe Commerce 2-Erweiterungen von [Commerce Marketplace](https://marketplace.magento.com/).     Wenn die widersprüchlichen Daten von einer Erweiterung stammen, die eigene Datenbankstrukturelemente hinzufügt, kann die Adobe Commerce 2-Version derselben Erweiterung solche Elemente zur Zieldatenbank (Adobe Commerce 2) hinzufügen, wodurch das Problem behoben wird.
* Verwenden Sie das `-a` Argument beim Ausführen des Tools, um Fehler automatisch zu beheben und zu verhindern, dass die Migration beendet wird.
* Konfigurieren Sie das Tool so, dass problematische Daten ignoriert werden.

Um Datenbankentitäten zu ignorieren, fügen Sie das `<ignore>`-Tag wie folgt zu einer Entität in der `map.xml` hinzu:

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
>Bevor Sie Entitäten anhand einer Zuordnungsdatei ignorieren oder die Option `-a` verwenden, stellen Sie sicher, dass Sie die betroffenen Daten nicht in Ihrem Adobe Commerce 2 -Speicher benötigen.

## Klasse ist im Datensatz nicht zugeordnet {#class-does-not-exist-but-mentioned}

### Fehlermeldung

```bash
Class <extension/class_name> is not mapped in record <attribute_id=196>
```

### Ursache

Eine Klasse aus der Adobe Commerce Adobe Commerce 1-Codebasis konnte während des [EAV-Migrationsschritts“ in unserer Entwicklerdokumentation nicht in ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/data-migration/basics/technical-specification) 2-Codebasis gefunden werden. In den meisten Fällen gehört die fehlende Klasse zu einer [Erweiterung](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/glossary#extension).

### Mögliche Lösungen

* Installieren Sie die entsprechende Adobe Commerce 2-Erweiterung.
* Ignorieren Sie das Attribut, das das Problem verursacht.    Fügen Sie dazu das Attribut zur `ignore` in der `eav-attribute-groups.xml.dist` hinzu.
* Hinzufügen der Klassenzuordnung mithilfe der `class-map.xml.dist`.

## Fremdschlüssel-Einschränkung schlägt fehl

### Text der Fehlermeldung

```bash
Foreign key <KEY_NAME> constraint fails on source database. Orphan records id: <id_1>, <id_2> from <child_table>.<field_id> has no referenced records in <parent_table>
```

### Ursache

In der `parent_table`, auf die der `field_id` der `child_table` verweist, fehlen Datenbankdatensätze.

### Mögliche Lösung

Löschen Sie die Datensätze aus dem `child_table` , wenn Sie sie nicht benötigen.

Um die Datensätze beizubehalten, deaktivieren Sie die `Data Integrity Step`, indem Sie die `config.xml` des Datenmigrations-Tools ändern.

## Duplikate bei URL-Neuschreibungen

```xml
There are duplicates in URL rewrites:
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/10
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/12
```

### Ursache

Die `Target path` in einer URL-Umschreibung muss durch ein eindeutiges Paar `Request path` + `Store ID` angegeben werden. Dieser Fehler meldet zwei Einträge, die dasselbe `Request path` + `Store ID` Paar mit zwei verschiedenen `Target path` verwenden.

### Mögliche Lösung

Aktivieren Sie die Option `auto_resolve_urlrewrite_duplicates` in Ihrer `config.xml`.

Diese Konfiguration fügt den widersprüchlichen Datensätzen von URL-Neuschreibungen eine Hash-Zeichenfolge hinzu und zeigt das Auflösungsergebnis in Ihrer Befehlszeilenschnittstelle an.

## Entitäten stimmen nicht überein {#mismatch-of-entities}

### Fehlermeldung

```bash
Mismatch of entities in the document: <DOCUMENT> Source: <COUNT_ITEMS_IN_SOURCE_TABLE> Destination: <COUNT_ITEMS_IN_DESTINATION_TABLE>
```

### Ursache

Der Fehler tritt während des Schritts zur Volumeprüfung auf. Dies bedeutet, dass die Anzahl der Adobe Commerce 2-Datensätze des Dokuments nicht mit der in Adobe Commerce 1 übereinstimmt.

Fehlende Datensätze treten auf, wenn ein Kunde während der Migration eine Bestellung aufgibt.

### Mögliche Lösung

Führen Sie das Datenmigrations-Tool im `Delta` aus, um inkrementelle Änderungen zu übertragen.

## Deltalog ist nicht installiert {#deltalog-is-not-installed}

### Fehlermeldung

```bash
Deltalog for <TABLE_NAME> is not installed
```

### Ursache

Dieser Fehler tritt während [inkrementellen Migration](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/data-migration/migrate-data/delta) (in unserer Entwicklerdokumentation) von Datenänderungen auf. Das bedeutet, dass Deltalogtabellen (mit dem Präfix `m2_cl_*`) nicht in der Adobe Commerce 1-Datenbank gefunden wurden. Das Tool installiert diese Tabellen während [Datenmigration](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/data-migration/migrate-data/data) (in unserer Entwicklerdokumentation) sowie Datenbank-Trigger, die Änderungen verfolgen und Deltalog-Tabellen ausfüllen.

Ein Grund für den Fehler könnte sein, dass Sie versuchen, von einer *Kopie* Ihres Adobe Commerce 1-Live-Stores und nicht vom Live-Store selbst zu migrieren. Wenn Sie eine Kopie aus einem Live Adobe Commerce 1-Store erstellen, der noch nie migriert wurde, enthält die Kopie nicht die Trigger und zusätzlichen Deltalogtabellen, die zum Abschließen einer Delta-Migration erforderlich sind, sodass die Migration fehlschlägt. Das Datenmigrations-Tool vergleicht NICHT die DB von AC1 und AC2, um die Unterschiede zu migrieren. Stattdessen verwendet das Tool die während der ersten Migration installierten Trigger und Deltalogtabellen, um nachfolgende Deltaimmigrationen durchzuführen. In einem solchen Fall enthält Ihre Live Copy der Adobe Commerce 1 DB nicht die Trigger- und Deltalogtabellen, die das Datenmigrations-Tool zur Durchführung einer Migration verwendet.

### Mögliche Lösung

Wir haben empfohlen, den Migrationsprozess aus einer Kopie Ihrer Adobe Commerce 1-Datenbank zu testen, um Ihre Migrationsprobleme zu beheben. Nachdem Sie die Probleme auf der Kopie behoben haben, starten Sie den Migrationsprozess von Ihrer Live Adobe Commerce 1-Datenbank erneut. Dies wird dazu beitragen, einen reibungslosen Migrationsprozess zu gewährleisten.

## Verwandtes Lesen

[Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook

