---
title: Zurückfallen auf [!DNL Elasticsearch7] bei Einstellung der Suchmaschine auf [!DNL Opensearch]
description: Dieser Artikel bietet eine Lösung für das Problem, wenn ein * Fallback auf [!DNL Elasticsearch7]* error occurs when the search engine is set to [!DNL OpenSearch] in Adobe Commerce erfolgt.
feature: Search
role: Developer
exl-id: 965d2929-5cf0-4e0a-9eed-6a656daaa120
source-git-commit: 6b8eecb3df0bb32344a5861a604a40402bb4d392
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# Zurückfallen auf [!DNL Elasticsearch7], wenn die Suchmaschine auf [!DNL Opensearch] gesetzt ist

Dieser Artikel bietet eine Lösung für das Problem, wenn ein *Fallback auf[!DNL Elasticsearch7]* -Fehler auftritt, wenn die Suchmaschine in Adobe Commerce auf [!DNL OpenSearch] gesetzt ist.

## Betroffene Versionen

Adobe Commerce auf Cloud-Infrastruktur 2.4.4 - 2.4.5

>[!NOTE]
>
>[!DNL OpenSearch] ist als Suchmaschine ab Adobe Commerce 2.4.6 verfügbar.

## Problem

Sie legen die **Suchmaschine** auf **[!DNL OpenSearch]** fest, sehen aber diesen Fehlertyp in der Datei `var/log/support_report.log`:

```[2024-04-04T00:27:41.212916+00:00] report.ERROR: opensearch search engine doesn't exist. Falling back to elasticsearch7 [] []```

<u>Zu reproduzierende Schritte</u>:

1. Stellen Sie sicher, dass [!DNL OpenSearch] installiert ist, indem Sie diesen Befehl ausführen: `curl 127.0.0.1:9200`<br>
Wenn dies auf *1.2.4* verweist, ist [!DNL OpenSearch] bereits installiert.
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Überprüfen Sie die Suchmaschine. Es wird [!DNL Elasticsearch7] angezeigt.

## Ursache

Obwohl Ihre Version [!DNL OpenSearch] unterstützt, erkennt/akzeptiert die Anwendung nur [!DNL Elasticsearch7] als Suchmaschine.

Ab Adobe Commerce-Version 2.4.6 wurde die Anwendung aktualisiert, damit [!DNL OpenSearch] als Suchmaschine ausgewählt werden kann.
Wenn Sie in einer Nicht-Cloud-Umgebung zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** gehen, können Sie diese Option ändern, wie in der folgenden **Lösung** dargestellt.
(Hinweis: In einer Cloud-Umgebung kann dieses Feld nicht geändert werden, da die Suchmaschine in der Datei `app/etc/env.php` gesperrt ist.)

## Lösung

Aktualisieren Sie die Variable `SEARCH_CONFIGURATION` in der Datei `.magento.env.yaml` und stellen Sie sicher, dass die Suchmaschine **3} auf *[!DNL elasticsearch7]* eingestellt ist.**

## Verwandtes Lesen

[Richten Sie den OpenSearch-Dienst](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) im Handbuch Commerce on Cloud Infrastructure ein.
