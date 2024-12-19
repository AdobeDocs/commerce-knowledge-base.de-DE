---
title: Behebung von nicht aktualisierten  [!DNL Commerce Data Exporter] - [!DNL cron] -Fehlern mit Changelog-Tabelle existiert nicht
description: Dieser Artikel bietet eine Lösung zur Behebung von Datensynchronisationsproblemen, die durch die Verwendung einer falschen Ansicht bei der Anmeldung  [!DNL Commerce Data Exporter mview]  werden.
feature: Data Import/Export, Saas, Logs
role: Developer
exl-id: 50f2223b-bfcf-4c3c-b0f1-dbcc4365edc2
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# Es wurden Daten behoben, die in [!DNL Commerce Data Exporter]-Feeds nicht aktualisiert wurden und [!DNL cron] Fehler in Änderungsprotokollen nicht vorhanden waren

Dieser Artikel bietet eine Lösung zur Behebung von Datensynchronisationsproblemen, die durch die Verwendung der falschen Ansicht-ID im [!DNL Data Exporter] [[!DNL Mview]](https://developer.adobe.com/commerce/php/development/components/indexing/#mview)-Abonnement verursacht wurden. Das [!DNL Mview]-Abonnement wird verwendet, um Änderungen für Datenbanktabellen zu verfolgen.

## Betroffene Produkte und Versionen

Adobe Commerce-Instanzen, bei denen benutzerdefinierter Code auf die Datenexportfunktion angewendet wurde (`commerce-data-exporter` oder `saas-exporter`). Der Fehler tritt auf, wenn die installierte [[!DNL SaaS] Datenexportversion 103.3.0](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes#release-6) oder höher ist und der Code direkt auf den `catalog_data_exporter_products` verweist.

## Problem

Händler stellen möglicherweise fest, dass Datenaktualisierungen in den Feed-Tabellen des Katalogs [!DNL Data Exporter] fehlen, und sehen die folgenden Fehler in den [!DNL cron]:

```
[2024-05-27T19:00:04.627604+00:00] report.ERROR: Cron Job indexer_clean_all_changelogs has an error: Table catalog_data_exporter_products_cl does not exist. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":305135616,"emalloc_start":283210384} [] [] 
```

## Ursache

Aufgrund von Namensänderungen in Feed-Tabellen, Indizes und Änderungsprotokolltabellen in der Version [!DNL Commerce Data Export] [Version 103.3.0](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes#release-9) funktionieren die [!DNL Mview]-Abonnements in benutzerdefinierten Erweiterungen, die [!DNL Commerce Data Export] Erweiterungen verwenden, möglicherweise nicht ordnungsgemäß.

In diesem Fall tritt der Fehler *Tabelle existiert nicht* auf, da der `catalog_data_exporter` Tabellenname in `cde_products_feed` geändert wurde, und Sie verfügen über benutzerdefinierten Code, der auf den alten Namen im [!DNL Data Exporter Mview]-Abonnement verweist.

## Lösung

Bearbeiten Sie in der angepassten Erweiterung die [!DNL Mview] Konfigurationsdatei (```./etc/mview.xml```), um den `catalog_data_exporter_products` Tabellennamen in *`cde_products_feed`* zu ändern.

Das folgende Beispiel zeigt den Code, der die vom [!DNL Mview]-Abonnement verfolgten Tabellen angibt:

```
<view id="cde_products_feed" class="Magento\CatalogDataExporter\Model\Indexer\ProductFeedIndexer" group="indexer">
     <subscriptions>
         <table name="custom_table" entity_column="product_id" />
     </subscriptions>
</view>
```

## Verwandtes Lesen

* [[!DNL SaaS] Versionshinweise zur Datenexporterweiterung](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes) im Adobe Commerce-Datenexporthandbuch für [!DNL SaaS] Services
* [Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook
