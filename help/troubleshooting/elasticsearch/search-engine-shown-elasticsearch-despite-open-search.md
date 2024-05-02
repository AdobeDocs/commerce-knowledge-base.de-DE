---
title: '[!DNL Elasticsearch] als Suchmaschine angezeigt wird, obwohl [!DNL OpenSearch] installation'
description: Dieser Artikel bietet eine Lösung für das Problem, bei dem [!DNL Elasticsearch] weiterhin als Suchmaschine für Adobe Commerce in Cloud angezeigt wird, auch wenn nach der Installation oder Aktualisierung auf [!DNL OpenSearch].
exl-id: cdd8a35d-da6f-46d3-b732-65626487c9bb
feature: Install
source-git-commit: 1a36e74807e6d32b0810416b6fb61aeca6f9be94
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# [!DNL Elasticsearch] als Suchmaschine angezeigt wird, obwohl [!DNL OpenSearch] Installation

Dieser Artikel bietet eine Lösung für das Problem, bei dem [!DNL Elasticsearch] weiterhin als Suchmaschine für Adobe Commerce in Cloud angezeigt wird, auch wenn nach der Installation oder Aktualisierung auf [!DNL OpenSearch].

## Betroffene Versionen

Adobe Commerce auf Cloud 2.4.3-p2 - 2.4.5-p6

>[!NOTE]
>
>[!DNL OpenSearch] ist als Suchmaschine ab Adobe Commerce 2.4.6 verfügbar.

## Problem

[!DNL Elasticsearch] weiterhin als Suchmaschine für Adobe Commerce in Cloud angezeigt wird, auch wenn nach der Installation oder Aktualisierung auf [!DNL OpenSearch].

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Überprüfen Sie die Suchmaschine. wird [!DNL Elasticsearch7].

## Ursache

Adobe Commerce ist fest codiert, um [!DNL Elasticsearch7] als Suchmaschine.

## Lösung

Überprüfen, ob [!DNL OpenSearch] installiert wurde, führen Sie den folgenden Befehl aus:

**Methode 1**:

* Führen Sie den folgenden Befehl auf dem Server aus: `curl 127.0.0.1:9200`. Sie sollte [!DNL OpenSearch] mit seiner Version.

**Methode 2**:

* Verwenden Sie den folgenden Befehl in der Magento-Cloud-CLI: `magento-cloud relationships -p <project_id>`. Suchen Sie nach dem Verwenden des Befehls [!DNL OpenSearch].

## Verwandtes Lesen

[Einrichten des OpenSearch-Dienstes](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) im Commerce on Cloud Infrastructure-Handbuch.
