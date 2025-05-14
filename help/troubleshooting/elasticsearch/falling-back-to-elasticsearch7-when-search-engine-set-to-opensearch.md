---
title: Fallback auf [!DNL Elasticsearch7]  wenn die Suchmaschine auf gesetzt ist [!DNL Opensearch]
description: Dieser Artikel bietet eine Lösung für das Problem, wenn in Adobe Commerce ein * [!DNL Elasticsearch7]* error occurs when the search engine is set to [!DNL OpenSearch]  auf verwendet wird.
feature: Search
role: Developer
exl-id: 965d2929-5cf0-4e0a-9eed-6a656daaa120
source-git-commit: d17af0f8f92726aa5a6914fc9e1ff13268256d04
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# Zurückfallen auf [!DNL Elasticsearch7], wenn die Suchmaschine auf [!DNL Opensearch] gesetzt ist

Dieser Artikel bietet eine Lösung für das Problem, wenn ein *Fallback auf[!DNL Elasticsearch7]* Fehler auftritt, wenn die Suchmaschine in Adobe Commerce auf [!DNL OpenSearch] eingestellt ist.

## Betroffene Versionen

Adobe Commerce auf Cloud-Infrastruktur
2.4.4 - 2.4.4-p12
2.4.5 - 2.4.5-P11

>[!NOTE]
>
>[!DNL OpenSearch] ist als Suchmaschine ab Adobe Commerce 2.4.6, 2.4.5-p12, 2.4.4-p13 verfügbar.

## Problem

Sie haben Ihre **Suchmaschine** auf **[!DNL OpenSearch]** festgelegt, aber diese Fehlerart ist in der `var/log/support_report.log`-Datei zu sehen:

```[2024-04-04T00:27:41.212916+00:00] report.ERROR: opensearch search engine doesn't exist. Falling back to elasticsearch7 [] []```

<u>Schritte zur Reproduktion</u>:

1. Stellen Sie sicher, dass [!DNL OpenSearch] installiert ist, indem Sie diesen Befehl ausführen: `curl 127.0.0.1:9200`<br>
Wenn *1.2.4* angegeben ist, ist [!DNL OpenSearch] bereits installiert.
1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Überprüfen Sie die Suchmaschine. Es wird [!DNL Elasticsearch7] zeigen.

## Ursache

Obwohl Ihre Version [!DNL OpenSearch] unterstützt, erkennt/akzeptiert die Anwendung nur [!DNL Elasticsearch7] als Suchmaschine.

Ab Adobe Commerce Version 2.4.6 wurde die Anwendung aktualisiert, damit [!DNL OpenSearch] als Suchmaschine ausgewählt werden kann.
Wenn Sie in einer Nicht-Cloud-Umgebung zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** gehen, können Sie diese Option wie in der **Lösung** unten dargestellt ändern.
(Hinweis: In einer Cloud-Umgebung kann dieses Feld nicht geändert werden, da die Suchmaschine in der `app/etc/env.php`-Datei gesperrt ist.)

## Lösung

Aktualisieren Sie die `SEARCH_CONFIGURATION` in der `.magento.env.yaml`-Datei und stellen Sie sicher, dass **Suchmaschine** auf *[!DNL elasticsearch7]* gesetzt ist.

## Verwandtes Lesen

[Richten Sie den OpenSearch-](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) im Handbuch zu Commerce in Cloud-Infrastrukturen ein.
