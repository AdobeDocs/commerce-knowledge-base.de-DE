---
title: Änderungen in der Datenbank werden nicht in der Storefront angezeigt
description: Dieser Artikel bietet Lösungen, um Verzögerungen oder Unterbrechungen bei der Anwendung von Entitätsaktualisierungen zu vermeiden. Dazu gehört auch, wie Sie vermeiden können, dass Log-Tabellen überdimensioniert werden, und wie Sie MySQL-Tabellen-Trigger einrichten.
exl-id: ac52c808-299f-4d08-902f-f87db1fa7ca6
feature: Catalog Management, Categories, Services, Storefront
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# Änderungen in der Datenbank werden nicht in der Storefront angezeigt

Dieser Artikel bietet Lösungen, um Verzögerungen oder Unterbrechungen bei der Anwendung von Entitätsaktualisierungen zu vermeiden. Dazu gehört auch, wie Sie vermeiden können, dass Log-Tabellen überdimensioniert werden, und wie Sie MySQL-Tabellen-Trigger einrichten.

Betroffene Produkte und Versionen:

* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x
* Adobe Commerce lokal 2.2.x, 2.3.x

## Problem

Änderungen, die Sie in der Datenbank vornehmen, werden nicht in der Storefront übernommen oder es gibt eine erhebliche Verzögerung bei der Anwendung von Entitätsaktualisierungen. Zu den betroffenen Entitäten gehören Produkte, Kategorien, Preise, Inventar, Katalogregeln, Verkaufsregeln und Zielregeln.

## Ursache

Wenn Ihre Indexer [konfiguriert, um nach Zeitplan zu aktualisieren](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html#configure-indexers), kann das Problem durch eine oder mehrere Tabellen verursacht werden, deren Änderungsprotokolle zu groß sind oder die MySQL-Trigger nicht eingerichtet sind.

### Oversized Änderungsprotokolltabellen

Die Änderungsprotokolltabellen werden größer, wenn die `indexer_update_all_views` Der Cron-Auftrag wird nicht mehrmals erfolgreich abgeschlossen.

Änderungsprotokolltabellen sind die Datenbanktabellen, in denen die Änderungen an Entitäten verfolgt werden. Ein Datensatz wird in einer Änderungsprotokolltabelle gespeichert, solange die Änderung nicht angewendet wird, was von der `indexer_update_all_views` Cron-Auftrag. Es gibt mehrere Änderungsprotokolltabellen in einer Adobe Commerce-Datenbank. Sie werden nach folgendem Muster benannt: INDEXER\_TABLE\_NAME + &#39;\_cl&#39;, beispielsweise `catalog_category_product_cl`, `catalog_product_category_cl`. Weitere Informationen dazu, wie Änderungen in der Datenbank verfolgt werden, finden Sie im [Indizierungsübersicht > Ansicht](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html#m2devgde-mview) in unserer Entwicklerdokumentation.

### MySQL-Datenbank-Trigger nicht eingerichtet

Wenn Sie nach dem Hinzufügen oder Ändern einer Entität (Trigger, Kategorie, Zielregel usw.) keine Datensätze zur entsprechenden Änderungsprotokolltabelle hinzugefügt haben, wird der Verdacht entstehen, dass keine Datensätze in der Datenbank eingerichtet werden.

## Lösung

>[!WARNING]
>
>Es wird dringend empfohlen, vor der Durchführung von Manipulationen eine Datenbanksicherung zu erstellen und diese bei hohen Seitenladezeiten zu vermeiden.

### Überdimensionierung von Änderungsprotokolltabellen vermeiden

Stellen Sie sicher, dass `indexer_update_all_views` Der Cron-Auftrag wurde immer erfolgreich abgeschlossen.

Sie können die folgende SQL-Abfrage verwenden, um alle fehlgeschlagenen Instanzen der `indexer_update_all_views` Cron-Auftrag:

```sql
select * from cron_schedule where job_code = "indexer_update_all_views" and status
  <> "success" and status <> "pending";
```

Sie können auch den Status in den Protokollen überprüfen, indem Sie nach der `indexer_update_all_views` Einträge:

* `<install_directory>/var/log/cron.log` - für Versionen 2.3.1+ und 2.2.8+
* `<install_directory>/var/log/system.log` - für frühere Versionen

### MySQL-Tabellen-Trigger neu festlegen

Um die fehlenden MySQL-Tabellen-Trigger einzurichten, müssen Sie den Indexermodus neu festlegen:

1. Wechseln Sie zu &quot;Bei Speichern&quot;.
1. Wechseln Sie zurück zu &quot;Ein Zeitplan&quot;.

Verwenden Sie den folgenden Befehl, um diesen Vorgang auszuführen.

>[!WARNING]
>
>Bevor Sie den Indexmodus wechseln, sollten Sie Ihre Website in [Wartung](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#maintenance-mode) Modus und [Cron-Aufträge deaktivieren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs) um Datenbanksperren zu vermeiden.

```bash
php bin/magento indexer:set-mode {realtime|schedule} [indexerName]
```

>[!INFO]
>
>Die mit Indexern verknüpften Datenbank-Trigger werden hinzugefügt, wenn der Indexermodus auf Planen gesetzt und entfernt wird, wenn der Indexermodus auf Echtzeit eingestellt ist. Wenn die Trigger in Ihrer Datenbank fehlen, während die Indexer auf einen Zeitplan eingestellt sind, ändern Sie die Indexer in Echtzeit und ändern Sie sie dann wieder zurück in den Zeitplan. Dadurch werden die Trigger zurückgesetzt.

## Verwandtes Lesen

<ul><li title="MySQL-Tabellen sind zu groß"><a href="/help/troubleshooting/database/mysql-tables-are-too-large.md">MySQL-Tabellen sind zu groß</a> in unserer Wissensdatenbank.</li>
<li title="MySQL-Tabellen sind zu groß"><a href="https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html#m2devgde-mview">Indexerübersicht &gt; Ansicht</a> in unserer Entwicklerdokumentation.</li></ul>
