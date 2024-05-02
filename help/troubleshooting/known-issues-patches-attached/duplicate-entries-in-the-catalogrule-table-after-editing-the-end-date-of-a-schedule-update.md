---
title: Duplizieren Sie Einträge in der Katalogregeltabelle, nachdem Sie das Enddatum einer geplanten Aktualisierung bearbeitet haben
description: Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce 2.2.3-Problem, bei dem das Bearbeiten des Enddatums oder der Uhrzeit eines Katalogpreisregelzeitplans dazu führt, dass der Tabelle "Katalogregel"doppelte Einträge hinzugefügt werden und Fehler in der Indexneu indizierung "catalogregel_rule"(Katalogregelprodukt) auftreten.
exl-id: e900b712-d0f5-4404-8441-64522035ce44
feature: Cache, Catalog Management, Marketing Tools
role: Developer
source-git-commit: 496151d1fe29a66d84349e4a96e7c5563a92c5c4
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---

# Duplizieren Sie Einträge in der Katalogregeltabelle, nachdem Sie das Enddatum einer geplanten Aktualisierung bearbeitet haben

Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce 2.2.3-Problem, bei dem das Bearbeiten des Enddatums oder der Uhrzeit eines Katalogpreisregel-Zeitplans dazu führt, dass beim Bearbeiten des Enddatums oder der Uhrzeit doppelte Einträge zum `catalogrule` und Fehler in der `catalogrule_rule` (Catalog Rule Product) Indexer neu indizieren.

## Problem

Wenn Sie das Enddatum oder die Uhrzeit einer Aktualisierung eines Katalogpreisregel ändern, werden doppelte Einträge in der Variablen `catalogrule` Datenbanktabelle. Daher wird die Variable `catalogrule_rule` Die Neuindizierung schlägt mit dem folgenden Fehler im Ausnahmeprotokoll fehl: *Element mit derselben ID ist bereits vorhanden*.

<u>Zu reproduzierende Schritte</u>:

Voraussetzungen: Die `catalogrule_rule` indexer ist auf *[Planmäßig aktualisieren](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration.html)* -Modus.

1. Erstellen Sie in Commerce Admin eine neue Katalogpreisregel unter **Marketing** > **Promotions** > **Katalogpreisregel**.
1. Im **Katalogpreisregel** Raster, klicken **Bearbeiten**, und planen Sie eine neue Aktualisierung und legen Sie **Status** nach *Aktiv.*
1. Klicks **Anzeigen/Bearbeiten** neben dem neu erstellten Update und ändern Sie das Enddatum in einen früheren Zeitpunkt.
1. Speichern Sie die Aktualisierung.
1. Führen Sie den reindex-Befehl für die `catalogrule_rule` Indexer.

<u>Erwartetes Ergebnis</u>:

Die `catalogrule_rule` Indexer wurde erfolgreich neu indiziert. Keine doppelten Einträge in der `catalogrule` Tabelle.

<u>Tatsächliches Ergebnis</u>:

Neuindizierung schlägt mit dem folgenden Fehler fehl: *Element mit derselben ID ist bereits vorhanden*, da in der `catalogrule` Tabelle.

## Lösung

Um das Problem zu lösen, müssen Sie den angehängten Patch anwenden und die vorhandenen duplizierten Einträge entfernen. Siehe [Duplizierte Einträge entfernen](#remove) im Abschnitt finden Sie Details zur Überprüfung, ob die Duplikate vorhanden sind und zum Entfernen.

## Patch

Der Patch ist an diesen Artikel angehängt. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[MDVA-10974\_EE\_2.2.3\_COMPOSER\_v2.patch herunterladen](assets/MDVA-10974_EE_2.2.3_COMPOSER_v2.patch.zip)

### Kompatible Adobe Commerce-Versionen:

Der Patch wurde für erstellt:

* Adobe Commerce 2.2.3

Der Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):

* Adobe Commerce auf Cloud-Infrastruktur 2.2.1 - 2.2.5
* Adobe Commerce vor Ort 2.2.1 - 2.2.2 und 2.2.4 - 2.2.5

## Anwenden des Pflasters

Siehe [Anwenden eines von Adobe bereitgestellten Composer-Patches](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) für Anweisungen in unserer Support-Wissensdatenbank.

## Duplizierte Einträge entfernen {#remove}

>[!NOTE]
>
>Bitte stellen Sie sicher, dass Sie vor allen Manipulationen ein aktuelles Backup haben.

Führen Sie die folgenden Schritte aus, um die duplizierten Einträge zu finden und zu löschen:

1. Führen Sie die folgende Abfrage aus, um zu überprüfen, ob die duplizierten Einträge in der Datenbank vorhanden sind:

   ```SQL
   SELECT entity_id, "catalog_product_entity" AS entity_table FROM catalog_product_entity GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT entity_id, "catalog_product_entity" AS entity_table FROM catalog_product_entity group by entity_id, updated_in having count(*) > 1    UNION    SELECT rule_id as entity_id, "catalogrule" AS entity_table FROM catalogrule GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT rule_id as entity_id, "catalogrule" AS entity_table FROM catalogrule GROUP BY entity_id, updated_in HAVING COUNT(*) > 1    UNION    SELECT rule_id as entity_id, "salesrule" AS entity_table FROM salesrule GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT rule_id as entity_id, "salesrule" AS entity_table FROM salesrule GROUP BY entity_id, updated_in HAVING COUNT(*) > 1    UNION    SELECT page_id as entity_id, "cms_page" AS entity_table FROM cms_page GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT page_id as entity_id, "cms_page" AS entity_table FROM cms_page GROUP BY entity_id, updated_in HAVING COUNT(*) > 1    UNION    SELECT block_id as entity_id, "cms_block" AS entity_table FROM cms_block GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT block_id as entity_id, "cms_block" AS entity_table FROM cms_block GROUP BY entity_id, updated_in HAVING COUNT(*) > 1;
   ```

   Wenn keine doppelten Einträge vorhanden sind, ist die Antwort leer und Sie müssen nichts anderes tun. Wenn die duplizierten Einträge vorhanden sind, erhalten Sie den Tabellennamen und `entity_id` der duplizierten Entität, wie im folgenden Beispiel gezeigt:

   ![table_results1.png](assets/table_results1.png)

   Beachten Sie, dass sich der Name des Felds mit der Entitäts-ID in bestimmten Tabellen von `entity_id`. Beispiel: in der `cms_page` table, würde es `page_id` anstelle von `entity_id`.

1. Als Nächstes müssen Sie sich die Duplikate genauer ansehen und wissen, welche entfernt werden sollen. Verwenden Sie eine ähnliche Abfrage wie die folgende, um die Duplikate anzuzeigen. Ersetzen Sie den Tabellennamen, den Namen der Entitäts-ID und den Wert entsprechend den Ergebnissen, die Sie im vorherigen Schritt erhalten haben.

   ```sql
   SELECT row_id, entity_id, created_in, updated_in FROM catalog_product_entity WHERE entity_id = 483 ORDER BY created_in;
   ```

   Sie erhalten eine Liste von Datensätzen mit mehreren Spalten. Beispiel:

   ![table_results2.png](assets/table_results2.png)

   Die `created_in` und `updated_in` -Werte sollten diesem Muster folgen: die `created_in` Wert der aktuellen Zeile ist gleich dem `updated_in` -Wert in der vorherigen Zeile. Außerdem wird die **erste Zeile** sollte created\_in = 1 enthalten und die **letzte Zeile** sollte aktualisierte_in = 2147483647 enthalten. (Wenn nur eine Zeile vorhanden ist, muss &quot;created\_in=1&quot;angezeigt werden. **und** aktualisiert\_in=2147483647). Die Zeilen, für die dieses Muster beschädigt ist, sollten gelöscht werden. In unserem Beispiel wäre dies die Zeile mit `row_id` =2052 als zweite und dritte Zeilen weisen denselben Wert für created_in auf: 1540837826, was nicht passieren sollte.

1. Löschen Sie das Duplikat mithilfe einer Abfrage, die der folgenden ähnelt. Ersetzen Sie den Tabellennamen, den Namen der Entitäts-ID und den Wert entsprechend den Ergebnissen, die Sie in den vorherigen Schritten erhalten haben:

   ```sql
   DELETE FROM catalog_product_entity WHERE entity_id = 483 AND row_id = 2052;
   ```

1. Cache durch Ausführen leeren:

   ```bash
   bin/magento cache:clean
   ```

   oder im Commerce Admin unter **System** > **Instrumente** > **Cacheverwaltung**.

## Nützliche Links in unserer Entwicklerdokumentation

* [Anwenden benutzerdefinierter Patches auf Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)
* [Anzeigen und Verwalten von Protokollen für Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html))

## Attached Files
