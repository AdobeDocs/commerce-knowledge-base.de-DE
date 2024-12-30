---
title: Elasticsearch 5 ist konfiguriert, aber die Suchseite wird nicht mit dem Fehler „Felddaten sind deaktiviert…“ geladen
description: 'In diesem Abschnitt wird beschrieben, wie Sie das Problem mit Elasticsearch 5 beheben, in dem die Suchseite nicht geladen wird und eine Ausnahme ähnlich der folgenden ausgelöst wird:'
exl-id: f5fa8144-4e7c-45ce-89d0-a8367e91d6db
feature: Cache
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Elasticsearch 5 ist konfiguriert, aber die Suchseite wird nicht mit dem Fehler „Felddaten sind deaktiviert…“ geladen

In diesem Abschnitt wird beschrieben, wie Sie das Problem mit Elasticsearch 5 beheben, in dem die Suchseite nicht geladen wird und eine Ausnahme ähnlich der folgenden ausgelöst wird:

```bash
{"0":"{\"error\":{\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}].
```

## Betroffene Versionen

* Adobe Commerce 2.2.x
* Elasticsearch v.5

>[!NOTE]
>
>Elasticsearch v.5 wird für Adobe Commerce 2.3.x nicht mehr unterstützt

## Problem

Voraussetzungen: Elasticsearch 5 ist konfiguriert.

Bei Suchanfragen wird die folgende Ausnahme in Protokollen generiert:

```bash
{"0":"{\"error\":{\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}].
```

## Ursache

Standardmäßig können in der mehrschichtigen Navigation nur bestimmte Arten von Produktattributen verwendet werden. Sie sind Ja/Nein, Dropdown, Mehrfachauswahl und Preis. Aus diesem Grund können Sie in der Commerce Admin kein Attribut eines anderen Typs als **Verwenden in mehrschichtiger Navigation** = *Filterbar* oder **Verwenden in Suchergebnissen - mehrschichtige Navigation** = *Ja* festlegen. Es gibt jedoch eine technische Möglichkeit, diese Einschränkung zu umgehen, indem die `is_filterable`- und `is_filterable_in_search` in der Datenbank direkt geändert werden. Wenn dies eintritt und ein anderer Attributtyp wie Datum, Text usw. für die Verwendung in der mehrschichtigen Navigation festgelegt ist, löst Elasticsearch 5 eine Ausnahme aus.

Um dies sicherzustellen, müssen Sie herausfinden, ob es andere Attribute als Dropdown, Multipleselect und Price gibt, die für die Verwendung in der mehrschichtigen Navigation festgelegt sind. Führen Sie die folgende Abfrage aus, um nach diesen Attributen zu suchen:

```sql
SELECT ea.attribute_code, ea.frontend_input, cea.is_filterable, cea.is_filterable_in_search FROM eav_attribute AS ea
    -> INNER JOIN catalog_eav_attribute AS cea ON ea.attribute_id = cea.`attribute_id`
    -> WHERE (is_filterable = 1 OR is_filterable_in_search = 1) AND frontend_input NOT IN ('boolean', 'multiselect', 'select', 'price');
```

Das Ergebnis enthält eine Liste von Attributen, die für die mehrschichtige Navigation verwendet werden und deren Typ dies nicht zulässt. Führen Sie die im folgenden Abschnitt beschriebenen Schritte aus, um dieses Problem zu beheben.

## Lösung

Um das Problem zu beheben, müssen Sie `is_filterable` (d. h. in der mehrschichtigen Navigation verwendet) und `filterable_in_search` (d. h. in den Suchergebnissen der mehrschichtigen Navigation verwendet) auf „0“ (nicht verwendet) festlegen. Gehen Sie dazu wie folgt vor:

1. Erstellen Sie eine Datenbanksicherung.
1. Verwenden Sie ein Datenbank-Tool wie [phpMyAdmin](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin) oder greifen Sie manuell über die Befehlszeile auf die Datenbank zu, um die folgende SQL-Abfrage auszuführen:

   ```sql
   UPDATE catalog_eav_attribute AS cea
       INNER JOIN eav_attribute AS ea
           ON ea.attribute_id = cea.attribute_id
   SET cea.is_filterable = 0, cea.is_filterable_in_search = 0
   WHERE (cea.is_filterable = 1 OR cea.is_filterable_in_search = 1)
       AND frontend_input NOT IN ('boolean', 'multiselect', 'select', 'price');
   ```

1. Führen Sie die vollständige Neuindizierung der Katalogsuche mit dem folgenden Befehl aus:

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. Cache durch Ausführen von bereinigen

   ```bash
   bin/magento cache:clean
   ```

oder in der Commerce Admin unter **System** > **Tools** > **Cache-Verwaltung**.

Jetzt sollten Sie in der Lage sein, ohne Probleme Katalogsuchen durchzuführen.
