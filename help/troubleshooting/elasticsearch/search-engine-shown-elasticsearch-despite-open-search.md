---
title: '''[!DNL Elasticsearch]'' wird trotz der [!DNL OpenSearch] Installation als Suchmaschine angezeigt.'
description: Dieser Artikel bietet eine Lösung für das Problem, dass [!DNL Elasticsearch] auch nach der Installation oder Aktualisierung auf [!DNL OpenSearch] weiterhin als Suchmaschine für Adobe Commerce in der Cloud angezeigt wird.
exl-id: cdd8a35d-da6f-46d3-b732-65626487c9bb
feature: Install
source-git-commit: 1f053f76ae56edc06bfe82e55210244c8ec4b8eb
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# [!DNL Elasticsearch] wird trotz der Installation von [!DNL OpenSearch] als Suchmaschine angezeigt

Dieser Artikel bietet eine Lösung für das Problem, dass [!DNL Elasticsearch] auch nach der Installation oder Aktualisierung auf [!DNL OpenSearch] weiterhin als Suchmaschine für Adobe Commerce in der Cloud angezeigt wird.

## Betroffene Versionen

Adobe Commerce auf Cloud 2.4.3-p2 - 2.4.5-p6

>[!NOTE]
>
>[!DNL OpenSearch] ist als Suchmaschine ab Adobe Commerce 2.4.6 verfügbar.

## Problem

[!DNL Elasticsearch] wird auch nach der Installation oder Aktualisierung auf [!DNL OpenSearch] weiterhin als Suchmaschine für Adobe Commerce in der Cloud angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Überprüfen Sie die Suchmaschine. Es wird [!DNL Elasticsearch7] angezeigt.

## Ursache

Adobe Commerce ist fest codiert, um [!DNL Elasticsearch7] als Suchmaschine anzugeben.

Dies ist nicht mit der installierten Version des Dienstes zu verwechseln. Die Anwendung erkennt nur [!DNL Elasticsearch7] als Suchmaschine, nicht jedoch [!DNL OpenSearch], obwohl sie den zugrunde liegenden [!DNL OpenSearch] -Dienst als Engine im Backend verwendet.

## Lösung

Um zu überprüfen, ob [!DNL OpenSearch] installiert wurde, führen Sie den folgenden Befehl aus:

**Methode 1**:

* Führen Sie den folgenden Befehl auf dem Server aus: `curl 127.0.0.1:9200`. Es sollte [!DNL OpenSearch] mit der Version zurückgeben.

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

* Verwenden Sie den folgenden Befehl in der Magento-Cloud-CLI: `magento-cloud relationships -p <project_id>`. Suchen Sie nach dem Verwenden des Befehls [!DNL OpenSearch].

## Verwandtes Lesen

[Richten Sie den OpenSearch-Dienst](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) im Handbuch Commerce on Cloud Infrastructure ein.
