---
title: Fehlerbehebung für das Produkt-Recommendations-Modul in Adobe Commerce
description: In diesem Artikel werden Vorschläge zur Fehlerbehebung für
exl-id: 431ee31e-eb5b-400c-9c99-cc86613453d7
feature: Cache, Compliance, Extensions, Marketing Tools, Personalization, Products, Recommendations
role: Developer
source-git-commit: b20ad74194bacb09116131f4a8da1006da75738a
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Fehlerbehebung für das Produkt-Recommendations-Modul in Adobe Commerce

In diesem Artikel werden Vorschläge zur Fehlerbehebung für

```php
magento/product-recommendations
```

-Modul und seine Abhängigkeit

```php
saas-export
```

-Modul, da Sie beide Module benötigen, um das Produkt-Recommendations-Tool in Adobe Commerce verwenden zu können.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.4.4 - 2.4.7

## Fehlerbehebung für das Modul &quot;Produktempfehlungen&quot;

Wenn Sie die

```php
magento/product-recommendations
```

richtig (Überprüfen Sie [Produkt-Recommendations - Installieren und Konfigurieren von Recommendations](https://devdocs.magento.com/recommendations/install-configure.html) in unserer Entwicklerdokumentation.). Es werden jedoch keine Empfehlungen angezeigt. Versuchen Sie Folgendes:

* Es ist möglich, dass das Modul nicht genügend Zeit hatte, Verhaltensdaten zu erfassen. Lassen Sie das System 24 Stunden laufen, damit es mit der Datenerfassung beginnen kann. Erwägen Sie die Bereitstellung eines Empfehlungstyps, für den keine Verhaltensdaten erforderlich sind, z. B. &quot;Mehr dazu&quot;.

* Wenn die von Ihnen konfigurierten Empfehlungen nicht angezeigt werden, sind möglicherweise noch nicht genügend Daten vorhanden, um Empfehlungen für den Benutzer zu erstellen.

* Stellen Sie sicher, dass der SaaS-Datenspeicher oder der API-Schlüssel gültig sind. Wenn bei der Initialisierung der Produktempfehlungen ein Fehler auftritt, nachdem Sie Ihren SaaS-Datenspeicher oder API-Schlüssel angegeben haben, überprüfen Sie, ob Sie den [SaaS-Datenraum und den API-Schlüssel](https://docs.magento.com/user-guide/configuration/services/saas.html) (in unserem Benutzerhandbuch) korrekt eingegeben haben. Um sicherzustellen, dass die MageID und der API-Schlüssel verknüpft sind, muss der Benutzer, der Eigentümer der MageID ist (normalerweise der Benutzer, der Inhaber der Adobe Commerce-Lizenz ist) derselbe Benutzer sein, der den API-Schlüssel generiert. Wenn Sie die verwendete MageID ändern müssen, senden Sie ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).[

>[!NOTE]
>
>Wenn der [Cookie-Beschränkungsmodus](https://docs.magento.com/m2/ce/user_guide/stores/compliance-cookie-restriction-mode.html) (in unserem Benutzerhandbuch) aktiviert ist, erfasst Adobe Commerce erst dann Verhaltensdaten, wenn der Käufer zustimmt. Wenn der Cookie-Beschränkungsmodus deaktiviert ist, erfasst Adobe Commerce standardmäßig Verhaltensdaten.

## Catalog SaaS-Exportmodul

Bei Problemen mit dem Katalog-SaaS-Export (

```php
saas-export
```

)-Modul:

1. Vergewissern Sie sich, dass die Aufträge für [cron](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-cron.html) (in unserer Entwicklerdokumentation) ausgeführt werden.
1. Vergewissern Sie sich, dass die [Indexer](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html) (in unserer Entwicklerdokumentation) ausgeführt werden und die    ```php    Product Feed    ```    indexer ist auf    ```php    Update by Schedule    ```    .
1. Vergewissern Sie sich, dass die Module aktiviert sind. Die    ```php    saas-export    ```    metappackage installiert die folgenden Module, die alle aktiviert werden müssen:    ```php    "magento/module-catalog-data-exporter"      "magento/module-catalog-inventory-data-exporter"      "magento/module-catalog-url-rewrite-data-exporter"      "magento/module-configurable-product-data-exporter"      "magento/module-data-exporter"      "magento/module-saas-catalog"    ```
1. Überprüfen Sie die [logs](https://devdocs.magento.com/guides/v2.3/config-guide/cli/logging.html) (in unserer Entwicklerdokumentation). Stellen Sie sicher, dass mit den oben genannten Modulen keine Fehler verbunden sind.
1. Aktualisieren Sie den Konfigurationscache. Wechseln Sie zu **System** > **Tools** > **Cache-Verwaltung** und leeren Sie den Konfigurations-Cache.
1. Vergewissern Sie sich, dass die    ```php    catalog_data_exporter_products    ```    Datenbanktabelle.

## Veranstaltungen

[Empfehlungsereignisse](https://devdocs.magento.com/recommendations/verify.html) in unserer Entwicklerdokumentation beschreibt die Verhaltensereignisse, die an Adobe Commerce gesendet werden.

## Verwandtes Lesen

* [Produkt-Recommendations - Überblick](https://devdocs.magento.com/recommendations/product-recs.html) in unserer Entwicklerdokumentation
* [Produkt-Recommendations - Installieren und Konfigurieren von Recommendations](https://devdocs.magento.com/recommendations/install-configure.html) in unserer Entwicklerdokumentation
* [Marketing - Produkt-Recommendations](https://docs.magento.com/m2/ee/user_guide/marketing/product-recommendations.html) in unserem Benutzerhandbuch
* [Erstellen Sie Produkt-Recommendations](https://docs.magento.com/m2/ee/user_guide/marketing/create-new-rec.html) in unserem Benutzerhandbuch
