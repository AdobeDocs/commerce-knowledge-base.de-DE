---
title: Es gibt mehrere Zeilen in der Datenbank für dieselbe Entität
description: Dieser Artikel bietet eine Lösung für das Problem, dass es mehrere Zeilen für dieselbe Entitäts-ID in der Datenbank gibt.
feature: Catalog Management, Categories, Services, Storefront
role: Developer
exl-id: 09d5c321-9c45-4041-b6f6-831efca0977e
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# Mehrere Zeilen in der Datenbank für dieselbe Entität

Dieser Artikel bietet eine Lösung für das Problem, dass es mehrere Zeilen für dieselbe Entitäts-ID in der Datenbank gibt.

## Betroffene Produkte und Versionen:

* Adobe Commerce (alle Versionen)

## Problem

Es gibt mehrere Zeilen für dieselbe Entitäts-ID in der Datenbank.

Beispiel: Nach Erhalt einer Liste von Datensätzen mit doppelten Entitäts-IDs bei Ausführung dieser Abfrage:

```
SELECT * FROM $entityTable WHERE $column = <$entityID> ORDER BY created_in;
```

Wo `$entityID = ID` der Kategorie/Produkt/Warenkorbpreisregel/Katalogpreisregel/CMS-Seite.

| Entität | $entityTable | $column |
|------------------|-----------------------------------|------------------|
| Kategorie/Produkt | catalog_category_entity/catalog_product_entity | entity_id |
| Regel zum Warenkorbpreis/Katalogpreis | salesrule/catalogrule | rule_id |
| CMS-Seite | cms_page | page_id |

## Ursache

Dies ist das erwartete Verhalten. Die verschiedenen Zeilen werden durch die Content Staging-Funktion erstellt:

* Wenn Sie ein Startdatum ohne Enddatum angeben, gibt es mindestens zwei Zeilen mit derselben Entitäts-/Regel-/Seiten-ID. Eine Zeile zeigt den ursprünglichen Status der Entität an (die Zeile, in der `created_in=1`) und eine Zeile zeigt die *Ende der geplanten Aktualisierung*.

* Wenn Sie ein Startdatum mit einem Enddatum angeben, gibt es mindestens drei Zeilen mit derselben Entität/Regel/Seiten-ID. Eine Zeile zeigt den ursprünglichen Status der Entität an (die Zeile, in der `created_in=1`), wird eine Zeile für die *Beginn der geplanten Aktualisierung* und eine Zeile für die *Ende der geplanten Aktualisierung*.

Beispiel: In dieser Abfrage:

```
SELECT row_id, entity_id, created_in, updated_in FROM catalog_product_entity WHERE entity_id = 483 ORDER BY created_in;
```

![multiple_rows_in_database.png](assets/multiple_rows_in_database.png)

* Die `created_in` und `updated_in` -Werte sollten diesem Muster folgen: Die `created_in` Wert der aktuellen Zeile ist gleich dem `updated_in` -Wert in der vorherigen Zeile. Außerdem sollte die erste Zeile `created_in = 1` und die letzte Zeile sollte `updated_in = 2147483647`. (Wenn es nur eine Zeile gibt, müssen Sie `created_in=1` und `updated_in=2147483647`).

### Warum wird der zweite DB-Eintrag (und alle nächsten) in DB für dieselbe Entität angezeigt?

* Der zweite DB-Datensatz (und möglicherweise die nächsten) für die betroffene Entität bedeutet, dass es Aktualisierungen für die Inhaltstaging-Umgebung gab, die mithilfe der `Magento_Staging` -Modul, das einen zusätzlichen Datensatz für eine Entität in den entsprechenden Tabellen erstellt.

Ein Problem tritt nur auf, wenn die Datensätze dieselben Werte für die `created_in` oder `updated_in` Spalten.

## Lösung

Dies ist das erwartete Verhalten und führt nur zu Problemen, wenn es Abweichungen zwischen den Zeilen gibt.

## Verwandtes Lesen

* [Änderungen an Kategorien werden nicht gespeichert](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/changes-to-categories-are-not-being-saved.html) in unserer Wissensdatenbank.
* [Duplizieren Sie Einträge in der Katalogregeltabelle, nachdem Sie das Enddatum einer geplanten Aktualisierung bearbeitet haben](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/duplicate-entries-in-the-catalogrule-table-after-editing-the-end-date-of-a-schedule-update.html) in unserer Wissensdatenbank.
