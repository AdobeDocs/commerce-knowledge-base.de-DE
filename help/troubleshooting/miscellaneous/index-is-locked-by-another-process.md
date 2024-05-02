---
title: Index wird durch einen anderen Prozess gesperrt
description: In diesem Artikel wird über ein gängiges Indizierungsproblem in Adobe Commerce gesprochen, bei dem der Index durch einen anderen Prozess gesperrt und übersprungen wird.
exl-id: 542c714c-fad5-4f0e-9757-d90044c36bfc
feature: Catalog Management, Categories
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Index wird durch einen anderen Prozess gesperrt

In diesem Artikel wird über ein gängiges Indizierungsproblem in Adobe Commerce gesprochen, bei dem der Index durch einen anderen Prozess gesperrt und übersprungen wird.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.X

## Problem

Während einer vollständigen Neuindizierung in Ihrer CLI erhalten Sie von Adobe Commerce die Fehlermeldung: *&#39;Index wird durch einen anderen Neuindizierungsprozess gesperrt. Überspringen.&quot;* Mit anderen Worten: Wenn der Prozess oder der Indextyp gesperrt ist, können Sie diesen bestimmten gesperrten Indextyp nicht neu indizieren. Die Neuindizierung überspringt diesen Indextyp immer.

## Ursache

Dieser Fehler konnte auftreten, wenn der vorherige Index nicht erfolgreich abgeschlossen wurde. Einige mögliche Gründe sind:

* Der Prozess wurde durch einen anderen Prozess oder Benutzer unterbrochen.
* Speicherbegrenzung.
* MySQL-Fehler, wie eine Zeitüberschreitung.
* Schwerwiegender PHP-Fehler während der Neuindizierung.

## Zu reproduzierende Schritte

1. Nehmen Sie beispielsweise Folgendes an:    ```bash    cataloginventory_stock ```    Der Indextyp ist gesperrt.
1. Wenn Sie versuchen, alle Daten durch Ausführen des CLI-Befehls neu zu indizieren    ```bash    php bin/magento indexer:reindex    ```, erhalten Sie das folgende Ausgabeergebnis:    ```bash    customer_grid index has been rebuilt successfully in 00:00:09    catalog_category_product index has been rebuilt successfully in 00:00:07    catalog_product_category index has been rebuilt successfully in 00:00:00    catalogrule_rule index has been rebuilt successfully in 00:00:05    catalog_product_attribute index has been rebuilt successfully in 00:00:04    cataloginventory_stock index is locked by another reindex process. Skipping.    catalog_product_price index has been rebuilt successfully in 00:00:01    catalogrule_product has been rebuilt successfully in 00:00:00    catalogsearch_fulltext index has been rebuilt successfully in 00:00:01    ```
1. Wie Sie oben sehen können, wird die    ```bash    cataloginventory_stock```    Der Indexprozess wurde übersprungen.


## Lösung

Sie müssen den Indexstatus zurücksetzen und dann versuchen, den neuen Neuindizierungsprozess auszuführen. Für den Status des Reset-Index müssen Sie den Befehl ausführen:

```bash
bin/magento indexer:reset <index identifier>
```

Wenn Sie sich nicht sicher sind, was die Indexkennungen (Code) sind, können Sie sie mithilfe des Befehls auflisten:

```bash
bin/magento indexer:info
```

Für die Vollständigkeit sind hier alle möglichen Kombinationen für native Indizes aufgeführt:

```bash
bin/magento indexer:reset design_config_grid;
bin/magento indexer:reset customer_grid;
bin/magento indexer:reset catalog_category_product;
bin/magento indexer:reset catalog_product_category;
bin/magento indexer:reset catalogrule_rule;
bin/magento indexer:reset catalog_product_attribute;
bin/magento indexer:reset cataloginventory_stock;
bin/magento indexer:reset catalog_product_price;
bin/magento indexer:reset catalogrule_product;
bin/magento indexer:reset catalogsearch_fulltext;
```


## Verwandtes Lesen

In unserer Support-Wissensdatenbank:

* [Cron-Aufgaben sperren Aufgaben anderer Gruppen (Adobe Commerce in der Cloud-Infrastruktur)](/help/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.md)

In unserem Benutzerhandbuch:

* [Indexverwaltung](https://docs.magento.com/user-guide/system/index-management.html?itm_source=merchdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=reindexing)

In unserer Entwicklerdokumentation:

* [Indizierungsübersicht](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html)
* [Best Practices für Indexer](https://devdocs.magento.com/guides/v2.3/performance-best-practices/configuration.html#indexers)
* [Cron konfigurieren und ausführen](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-cron.html)
* [Indexer verwalten](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html)
* [Indexer-Optimierung](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexer-batch.html)
