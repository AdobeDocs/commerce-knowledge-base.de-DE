---
title: Fehlerkorrektur - In [!DNL Commerce Data Exporter] Feeds werden keine Daten aktualisiert und in [!DNL cron] Protokollfehlern mit der Änderungstabelle sind keine Änderungen vorhanden
description: Dieser Artikel bietet eine Lösung zum Beheben von Datensynchronisierungsproblemen, die durch die Verwendung der falschen Ansichts-ID im [!DNL Commerce Data Exporter mview] Abonnement verursacht werden.
feature: Data Import/Export, Saas, Logs
role: Developer
source-git-commit: cf87b5f1280a2d1d23c7ace37616feb337b5142f
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# Fehlerbehebungsdaten, die in [!DNL Commerce Data Exporter] Feeds nicht aktualisiert wurden und Fehler in [!DNL cron]-Protokollen mit der Änderungstabelle nicht vorhanden sind

Dieser Artikel bietet eine Lösung zum Beheben von Datensynchronisierungsproblemen, die durch die Verwendung der falschen Ansichts-ID im [!DNL Data Exporter] [[!DNL Mview]](https://developer.adobe.com/commerce/php/development/components/indexing/#mview) -Abonnement verursacht werden. Das Abonnement [!DNL Mview] wird verwendet, um Änderungen an Datenbanktabellen zu verfolgen.

## Betroffene Produkte und Versionen

Adobe Commerce-Instanzen, bei denen benutzerdefinierter Code auf die Datenexport-Funktion (`commerce-data-exporter` oder `saas-exporter`) angewendet wurde. Der Fehler tritt auf, wenn die installierte Version von [[!DNL SaaS] Datenexport 103.3.0](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes#release-6) oder höher ist und der Code direkt auf den Index `catalog_data_exporter_products` verweist.

## Problem

Merchandising kann feststellen, dass Datenaktualisierungen in den Feed-Tabellen des Katalogs [!DNL Data Exporter] fehlen, und die folgenden Fehler werden in den [!DNL cron]-Auftragsprotokollen angezeigt:

```
[2024-05-27T19:00:04.627604+00:00] report.ERROR: Cron Job indexer_clean_all_changelogs has an error: Table catalog_data_exporter_products_cl does not exist. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":305135616,"emalloc_start":283210384} [] [] 
```

## Ursache

Aufgrund von Namensänderungen in Feed-Tabellen, Indizes und Log-Tabellen in der Version [!DNL Commerce Data Export] [1, Version 103.3.0](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes#release-9) können die [!DNL Mview] Abonnements in benutzerdefinierten Erweiterungen, die [!DNL Commerce Data Export] -Erweiterungen verwenden, möglicherweise nicht ordnungsgemäß funktionieren.

In diesem Fall tritt der Fehler *table ist nicht vorhanden* auf, da der Name der `catalog_data_exporter`-Tabelle in `cde_products_feed` geändert wurde. Sie haben benutzerdefinierten Code, der auf den alten Namen im [!DNL Data Exporter Mview]-Abonnement verweist.

## Lösung

Bearbeiten Sie in der angepassten Erweiterung die Konfigurationsdatei [!DNL Mview] (```./etc/mview.xml```), um den Tabellennamen `catalog_data_exporter_products` in *`cde_products_feed`* zu ändern.

Das folgende Beispiel zeigt den Code, der die vom [!DNL Mview] -Abonnement verfolgten Tabellen angibt:

```
<view id="cde_products_feed" class="Magento\CatalogDataExporter\Model\Indexer\ProductFeedIndexer" group="indexer">
     <subscriptions>
         <table name="custom_table" entity_column="product_id" />
     </subscriptions>
</view>
```

## Verwandtes Lesen

[[!DNL SaaS] Versionshinweise zur Datenexport-Erweiterung](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes) im Adobe Commerce-Datenexportleitfaden für [!DNL SaaS] -Dienste.
