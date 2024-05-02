---
title: Fallback zu [!DNL Elasticsearch7] wenn die Suchmaschine auf [!DNL Opensearch]
description: Dieser Artikel bietet eine Lösung für das Problem, wenn ein * Fallback auf [!DNL Elasticsearch7]* error occurs when the search engine is set to [!DNL OpenSearch] in Adobe Commerce.
feature: Search
role: Developer
exl-id: 965d2929-5cf0-4e0a-9eed-6a656daaa120
source-git-commit: 6b8eecb3df0bb32344a5861a604a40402bb4d392
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# Fallback zu [!DNL Elasticsearch7] wenn die Suchmaschine auf [!DNL Opensearch]

Dieser Artikel bietet eine Lösung für das Problem, wenn ein *Fallback zu[!DNL Elasticsearch7]* Fehler tritt auf, wenn die Suchmaschine auf [!DNL OpenSearch] in Adobe Commerce.

## Betroffene Versionen

Adobe Commerce auf Cloud-Infrastruktur 2.4.4 - 2.4.5

>[!NOTE]
>
>[!DNL OpenSearch] ist als Suchmaschine ab Adobe Commerce 2.4.6 verfügbar.

## Problem

Sie legen **Suchmaschine** nach **[!DNL OpenSearch]**, aber sehen Sie diesen Fehlertyp im `var/log/support_report.log` Datei:

```[2024-04-04T00:27:41.212916+00:00] report.ERROR: opensearch search engine doesn't exist. Falling back to elasticsearch7 [] []```

<u>Zu reproduzierende Schritte</u>:

1. Stellen Sie sicher, dass [!DNL OpenSearch] wird durch Ausführen dieses Befehls installiert: `curl 127.0.0.1:9200`<br>
Wenn *1.2.4*, dann [!DNL OpenSearch] ist bereits installiert.
1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Überprüfen Sie die Suchmaschine. wird [!DNL Elasticsearch7].

## Ursache

Auch wenn Ihre Version [!DNL OpenSearch], erkennt die Anwendung nur [!DNL Elasticsearch7] als Suchmaschine.

Ab Adobe Commerce-Version 2.4.6 wurde die Anwendung aktualisiert, um [!DNL OpenSearch] als Suchmaschine auszuwählen.
Wenn Sie **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** In einer Nicht-Cloud-Umgebung können Sie diese Option ändern, wie in der **Lösung** unten.
(Hinweis: In einer Cloud-Umgebung kann dieses Feld nicht geändert werden, da die Suchmaschine im `app/etc/env.php` Datei.)

## Lösung

Aktualisieren Sie die `SEARCH_CONFIGURATION` in der `.magento.env.yaml` und stellen Sie sicher, dass die **Suchmaschine** auf *[!DNL elasticsearch7]*.

## Verwandtes Lesen

[Einrichten des OpenSearch-Dienstes](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) im Commerce on Cloud Infrastructure-Handbuch.
