---
title: '[!DNL Elasticsearch] wird trotz Installation als  [!DNL OpenSearch]  angezeigt'
description: Dieser Artikel bietet eine Lösung für das Problem [!DNL Elasticsearch]  bei dem weiterhin als Suchmaschine für Adobe Commerce in der Cloud angezeigt wird, auch nach der Installation oder dem Upgrade auf [!DNL OpenSearch].
exl-id: cdd8a35d-da6f-46d3-b732-65626487c9bb
feature: Install
source-git-commit: b3f68e43ce3c4fdea001db1d8ba2774900db7dba
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# [!DNL Elasticsearch] wird trotz [!DNL OpenSearch] Installation als Suchmaschine angezeigt

Dieser Artikel bietet eine Lösung für das Problem, dass [!DNL Elasticsearch] auch nach der Installation oder Aktualisierung auf [!DNL OpenSearch] weiterhin als Suchmaschine für Adobe Commerce in der Cloud angezeigt wird.

## Betroffene Versionen

Adobe Commerce in Cloud 2.4.4 - 2.4.5-p11

>[!NOTE]
>
>[!DNL OpenSearch] ist ab Adobe Commerce 2.4.6 als Suchmaschine verfügbar.

## Problem

[!DNL Elasticsearch] wird auch nach der Installation oder dem Upgrade auf [!DNL OpenSearch] weiterhin als Suchmaschine für Adobe Commerce on Cloud angezeigt.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Überprüfen Sie die Suchmaschine. Es wird [!DNL Elasticsearch7] zeigen.

## Ursache

[!DNL Elasticsearch7] ist in Adobe Commerce als Suchmaschine für diese Versionen hartcodiert.

Dies ist nicht mit der installierten Version des Dienstes zu verwechseln. Obwohl im Code kein [!DNL Opensearch] enthalten ist, kann Adobe Commerce den zugrunde liegenden [!DNL Opensearch]-Service verwenden.

## Lösung

Um zu überprüfen, ob [!DNL OpenSearch] installiert wurde, führen Sie den folgenden Befehl aus:

**Methode 1**:

* Führen Sie den folgenden Befehl auf dem Server aus: `curl 127.0.0.1:9200`. Sie sollte [!DNL OpenSearch] mit ihrer Version zurückgeben.

Beispiel:

```
$ curl 127.0.0.1:9200
{
  "name" : $clusterName,
  "cluster_name" : "opensearch_stg",
  "cluster_uuid" : $clusterUuid,
  "version" : {
    "distribution" : "opensearch",
    "number" : "1.2.4",
    "build_type" : "deb",
    "build_hash" : "44ccdbaed5fe5a8b02d99a611857a671b6dd909d",
    "build_date" : "2022-11-08T09:23:45.993372Z",
    "build_snapshot" : false,
    "lucene_version" : "8.10.1",
    "minimum_wire_compatibility_version" : "6.8.0",
    "minimum_index_compatibility_version" : "6.0.0-beta1"
  },
  "tagline" : "The OpenSearch Project: https://opensearch.org/"
}
```

**Methode 2**:

* Verwenden Sie den folgenden Befehl auf der Magento-Cloud-CLI: `magento-cloud relationships -p <project_id>`. Suchen Sie nach [!DNL OpenSearch], nachdem Sie den Befehl verwendet haben.

## Verwandtes Lesen

[Richten Sie den OpenSearch-](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) im Handbuch zu Commerce in Cloud-Infrastrukturen ein.
