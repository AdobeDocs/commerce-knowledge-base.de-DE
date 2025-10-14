---
title: Index wird durch einen anderen Prozess gesperrt
description: In diesem Artikel wird über ein häufiges Indizierungsproblem in Adobe Commerce gesprochen, bei dem der Index durch einen anderen Prozess gesperrt und übersprungen wird.
exl-id: 542c714c-fad5-4f0e-9757-d90044c36bfc
feature: Catalog Management, Categories
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Index wird durch einen anderen Prozess gesperrt

In diesem Artikel wird über ein häufiges Indizierungsproblem in Adobe Commerce gesprochen, bei dem der Index durch einen anderen Prozess gesperrt und übersprungen wird.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.x

## Problem

Während einer vollständigen Neuindizierung in Ihrer CLI erhalten Sie von Adobe Commerce die Fehlermeldung: *&#39;index is locked by another reindex process. Wird übersprungen.“* heißt, wenn der Prozess oder der Indextyp gesperrt ist, können Sie diesen bestimmten gesperrten Indextyp nicht neu indizieren. Die Neuindizierung überspringt immer diesen Indextyp.

## Ursache

Dieser Fehler kann auftreten, wenn der vorherige Index nicht erfolgreich abgeschlossen wurde. Einige mögliche Gründe sind:

* Der Prozess wurde durch einen anderen Prozess oder Benutzer unterbrochen.
* Speicherlimit.
* MySQL-Fehler, wie eine Zeitüberschreitung.
* Schwerwiegender PHP-Fehler während der Neuindizierung.

## Schritte zur Reproduktion

1. Beispiel: Die Variable    ```bash    cataloginventory_stock ```    Indextyp ist gesperrt.
1. Beim Versuch, alle Daten durch Ausführen des CLI-Befehls neu zu indizieren    ```bash    php bin/magento indexer:reindex    ``` erhalten Sie das folgende Ausgabeergebnis:    ```bash    customer_grid index has been rebuilt successfully in 00:00:09    catalog_category_product index has been rebuilt successfully in 00:00:07    catalog_product_category index has been rebuilt successfully in 00:00:00    catalogrule_rule index has been rebuilt successfully in 00:00:05    catalog_product_attribute index has been rebuilt successfully in 00:00:04    cataloginventory_stock index is locked by another reindex process. Skipping.    catalog_product_price index has been rebuilt successfully in 00:00:01    catalogrule_product has been rebuilt successfully in 00:00:00    catalogsearch_fulltext index has been rebuilt successfully in 00:00:01    ```
1. Wie Sie oben sehen können, ist die    ```bash    cataloginventory_stock```    Der Indexprozess wurde übersprungen.


## Lösung

Sie müssen den Indexstatus zurücksetzen und dann versuchen, den neuen Neuindizierungsprozess auszuführen. Um den Indexstatus zurückzusetzen, müssen Sie den Befehl ausführen:

```bash
bin/magento indexer:reset <index identifier>
```

Wenn Sie sich nicht sicher sind, was die Indexkennungen (Code) sind, können Sie sie mit dem Befehl auflisten:

```bash
bin/magento indexer:info
```

Der Vollständigkeit halber finden Sie hier alle möglichen Kombinationen für native Indizes:

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

* [Cron-Aufgaben sperren Aufgaben von anderen Gruppen (Adobe Commerce auf Cloud-Infrastruktur)](/help/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.md)

In unserem Benutzerhandbuch:

* [Indexverwaltung](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/tools/index-management?itm_source=merchdocs&itm_medium=search_page&itm_campaign=federated_search&itm_term=reindexing)

In unserer Entwicklerdokumentation:

* [Indizierungsübersicht](https://developer.adobe.com/commerce/php/development/components/indexing/)
* [Best Practices für Indexer](https://experienceleague.adobe.com/de/docs/commerce-operations/performance-best-practices/configuration)
* [Konfigurieren und Ausführen von Cron](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs)
* [Indexer verwalten](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/cli/manage-indexers)
* [Indexeroptimierung](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/)
