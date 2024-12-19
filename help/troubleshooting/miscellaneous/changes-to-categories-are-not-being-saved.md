---
title: Änderungen an Kategorien werden nicht gespeichert
description: Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass beim Aktualisieren von Produktkategorien über den Commerce-Admin die Änderungen nicht in der Admin- und Storefront angezeigt werden. Das Problem wird durch die beschädigten Daten in der Tabelle „CATALOG_CATEGORY_ENTITY“ verursacht. Um das Problem zu beheben, beheben oder entfernen Sie die problematischen Datensätze für die Kategorieaktualisierung in der Tabelle. Danach sollten Sie in der Lage sein, Produktkategorien mithilfe des Administrators zu aktualisieren.
exl-id: d951205c-add9-478c-9c7d-2ba975d53b14
feature: Categories
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 0%

---

# Änderungen an Kategorien werden nicht gespeichert

Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass beim Aktualisieren von Produktkategorien über den Commerce-Admin die Änderungen nicht in der Admin- und Storefront angezeigt werden. Das Problem wird durch die beschädigten Daten in der `catalog_category_entity` verursacht. Um das Problem zu beheben, beheben oder entfernen Sie die problematischen Datensätze für die Kategorieaktualisierung in der Tabelle. Danach sollten Sie in der Lage sein, Produktkategorien mithilfe des Administrators zu aktualisieren.

## Problem

Nachdem Sie Änderungen an einer Produktkategorie im Admin- und Speicherbereich vorgenommen haben, werden die neuen Aktualisierungen weder gespeichert noch in der Admin- und Storefront angezeigt.

### Schritte zur Reproduktion

1. Navigieren Sie **Katalog** > **Kategorien**.
1. Kategorie auswählen.
1. Nehmen Sie Änderungen vor und klicken Sie dann auf **Speichern**.
1. Die Meldung wird angezeigt: *Sie haben die Kategorie gespeichert*.
1. Beachten Sie, dass die von Ihnen vorgenommene Änderung nicht gespeichert wurde.

## Mögliche Ursache: Beschädigte Daten in der `catalog_category_entity`

Das Problem wird durch dieselben Werte in der Spalte `created_in` der betroffenen Kategoriedatensätze in der Datenbank verursacht (DB).

![Beschädigte Daten in der Tabelle catalog_category_entity](assets/catalog_category_entity.png)

Details:

* Die `catalog_category_entity` DB-Tabelle enthält zwei oder mehr Datensätze für die betroffene Kategorie (diese Datensätze haben denselben `entity_id`).
* Diese Kategoriedatensätze haben **dieselben Werte in der `created_in` Spalte**.

### Wie wird der zweite DB-Eintrag (und alle nächsten) in der DB für ein und dieselbe Kategorie angezeigt?

Der zweite DB-Eintrag (und möglicherweise die nächsten) für die betroffene Kategorie bedeutet, dass Kategorienaktualisierungen mit dem Magento\_Staging-Modul geplant wurden. Das Modul erstellt einen zusätzlichen Datensatz für eine Kategorie im `catalog_category_entity`. Dies ist das erwartete Anwendungsverhalten. Das Problem besteht darin, dass die Datensätze dieselben Werte für die `created_in` Spalte aufweisen.

### Wie werden dieselben Werte angezeigt?

Wir können die Gründe für die Datenbeschädigung nicht mit Sicherheit angeben. Mögliche Gründe können sein:

* Anpassungen (Code, Designs usw.)
* Falsche Datenmigration
* Falsche Datenwiederherstellung aus der Sicherung

Nach unserem Kenntnisstand ist eine solche Datenbeschädigung nicht typisch für die „bereinigte“ (vordefinierte) Adobe Commerce-Instanz und kann nicht ohne Anpassungen auf einer Adobe Commerce-Installation reproduziert werden.

### Überprüfen, ob dies Ihr Problem ist

Die `catalog_category_entity` Tabelle sollte mehrere Datensätze für die betroffene Kategorie enthalten (Datensätze sollten denselben `entity_id` haben) und mindestens zwei dieser Datensätze sollten dieselben `created_in` Werte haben. Bei diesem Vorgang werden die geplanten Aktualisierungen des Staging nicht im Commerce Admin angezeigt, sondern es wird nur der leere Block Geplante Änderungen angezeigt.

#### Zu überprüfende Schritte

1. Zugreifen auf die Tabelle catalog\_category\_entity in Ihrer Datenbank
1. Entitäten nach entity\_id filtern, wobei entity\_id die betroffene Kategorie identifiziert.
1. Wenn die Werte in der Spalte Erstellt\_in für verschiedene Einträge mit derselben entity\_id gleich sind, ist dies der Fall. Normalerweise sind die `created_in` für jeden Datensatz unterschiedlich.

![Beschädigte Daten in der Tabelle catalog_category_entity](assets/catalog_category_entity.png)

## Lösung

Sie können eine der folgenden Lösungen wählen:

1. **Löschen** der Datensätze zur Aktualisierung der problematischen Kategorien
1. **Reparieren** der Datensätze für die Aktualisierung der problematischen Kategorien

### Löschen der Einträge zur Aktualisierung der problematischen Kategorien

In dieser Lösung müssen Sie den richtigen `updated_in` für den ursprünglichen Kategoriedatensatz festlegen und alle anderen Datensätze für diese Kategorie löschen. Dadurch werden alle geplanten Kategorieaktualisierungen entfernt.

Führen Sie die folgenden Schritte aus:

1. Suchen Sie die DB-Datensätze mit dem `entity_id` der betroffenen Kategorie.
1. Wählen Sie den Datensatz mit der größten Ganzzahl in der Spalte `updated_in` aus.
1. Kopieren Sie den `updated_in` aus dem ausgewählten Datensatz.
1. Wählen Sie den Datensatz mit `row_id` = `entity_id` aus (erster Kategoriedatensatz) und fügen Sie den kopierten Wert in die `updated_in` Spalte dieses Datensatzes ein.
1. Zeile(n) mit `row_id` ungleich `entity_id` löschen.

### Reparieren der Einträge für die Aktualisierung problematischer Kategorien

1. Suchen Sie die Kategoriedatensätze mit demselben `entity_id` und demselben `created_in`.
1. Wählen Sie den Datensatz aus, bei dem `row_id` = `entity_id`, und kopieren Sie den `updated_in`.
1. Wählen Sie den Datensatz aus, bei dem `row_id` nicht gleich `entity_id` ist, und fügen Sie den kopierten `updated_in` als `created_in` ein. Siehe den Screenshot unten als Illustration.    ![Kopieren der Datei created_in value.png](assets/copy_created-in_value.png)
1. Überprüfen Sie, ob der Kategorie-Update-Datensatz, dessen `created_in` Sie aktualisiert haben (in Schritt 3), in der `staging_update` vorhanden ist. *Beispiel:* WENN der kopierte `created_in`-Wert 1509281953 ist, MUSS die Entität mit `row_id` = 1509281953 in der `staging_update`-Tabelle vorhanden sein.

## Verwandtes Lesen

[Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook
