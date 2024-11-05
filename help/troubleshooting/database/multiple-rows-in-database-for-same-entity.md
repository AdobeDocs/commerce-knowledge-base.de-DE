---
title: Es gibt mehrere Zeilen in der Datenbank für dieselbe Entität
description: Dieser Artikel bietet eine Lösung für das Problem, dass es mehrere Zeilen für dieselbe Entitäts-ID in der Datenbank gibt.
feature: Catalog Management, Categories, Services, Storefront
role: Developer
exl-id: 09d5c321-9c45-4041-b6f6-831efca0977e
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '444'
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

Wobei `$entityID = ID` von Kategorie/Produkt/Warenkorbpreisregel/Katalogpreisregel/CMS-Seite ist.

| Entität | $entityTable | $column |
|------------------|-----------------------------------|------------------|
| Kategorie/Produkt | catalog_category_entity/catalog_product_entity | entity_id |
| Regel zum Warenkorbpreis/Katalogpreis | salesrule/catalogrule | rule_id |
| CMS-Seite | cms_page | page_id |

## Ursache

Dies ist das erwartete Verhalten. Die verschiedenen Zeilen werden durch die Content Staging-Funktion erstellt:

* Wenn Sie ein Startdatum ohne Enddatum angeben, gibt es mindestens zwei Zeilen mit derselben Entitäts-/Regel-/Seiten-ID. Eine Zeile gibt den ursprünglichen Status der Entität an (die Zeile, in der `created_in=1` ist), und eine Zeile zeigt das *Ende der geplanten Aktualisierung* an.

* Wenn Sie ein Startdatum mit einem Enddatum angeben, gibt es mindestens drei Zeilen mit derselben Entität/Regel/Seiten-ID. Eine Zeile gibt den ursprünglichen Status der Entität an (die Zeile, in der `created_in=1` ist), eine Zeile den *Start des geplanten Updates* und eine Zeile den *Ende des geplanten Updates*.

Beispiel: In dieser Abfrage:

```
SELECT row_id, entity_id, created_in, updated_in FROM catalog_product_entity WHERE entity_id = 483 ORDER BY created_in;
```

![multiple_rows_in_database.png](assets/multiple_rows_in_database.png)

* Die Werte `created_in` und `updated_in` sollten diesem Muster folgen: Der `created_in` Wert der aktuellen Zeile entspricht dem `updated_in` Wert in der vorherigen Zeile. Außerdem sollte die erste Zeile `created_in = 1` und die letzte Zeile `updated_in = 2147483647` enthalten. (Wenn es nur eine Zeile gibt, müssen Sie `created_in=1` und `updated_in=2147483647` sehen.)

### Warum wird der zweite DB-Eintrag (und alle nächsten) in DB für dieselbe Entität angezeigt?

* Der zweite DB-Datensatz (und möglicherweise die nächsten) für die betroffene Entität bedeutet, dass mit dem `Magento_Staging` -Modul geplante Content Staging-Aktualisierungen vorgenommen wurden, die einen zusätzlichen Datensatz für eine Entität in den entsprechenden Tabellen erstellen.

Ein Problem würde nur auftreten, wenn die Datensätze dieselben Werte für die Spalten `created_in` oder `updated_in` aufweisen.

## Lösung

Dies ist das erwartete Verhalten und führt nur zu Problemen, wenn es Abweichungen zwischen den Zeilen gibt.

## Verwandtes Lesen

* [Änderungen an Kategorien werden nicht in unserer Support-Wissensdatenbank gespeichert](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/changes-to-categories-are-not-being-saved.html)
* [Duplizieren Sie Einträge in der Katalogregeltabelle, nachdem Sie das Enddatum eines Zeitplanaktualisierens bearbeitet haben](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/duplicate-entries-in-the-catalogrule-table-after-editing-the-end-date-of-a-schedule-update.html) in unserer Support-Wissensdatenbank
* [Best Practices für die Änderung von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Playbook für die Commerce-Implementierung
