---
title: Fehler [!DNL opensearch] Suchmaschine existiert nicht. Fallback zu [!DNL livesearch].
description: Dieser Artikel bietet eine Lösung für das Problem, bei dem der Fehler "Error- [!DNL opensearch] Suchmaschine existiert nicht. Fallback zu [!DNL livesearch]." in Adobe Commerce über die Cloud-Infrastruktur.
feature: Deploy, Search
role: Developer
exl-id: a6cc981d-b8f0-402d-8771-60d2f21f09f8
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---

# Fehler [!DNL opensearch] Suchmaschine existiert nicht. Fallback zu [!DNL livesearch].

Dieser Artikel bietet eine Lösung für das Problem, bei dem der Fehler angezeigt wird: *Fehler: [!DNL opensearch] Suchmaschine existiert nicht. Fallback zu [!DNL livesearch].* in Adobe Commerce in der Cloud-Infrastruktur [!DNL Live Search] verwendet.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle Versionen
* [!DNL Live Search] installiert und verwendet wird

## Problem

Die folgende Meldung wird in den Protokollen angezeigt (und kann in [!DNL New Relic]):
*Fehler: [!DNL opensearch] Suchmaschine existiert nicht. Fallback zu [!DNL livesearch].*

## Lösung

1. Ändern Sie die `.magento.env.yaml` -Datei.
1. Suchen Sie die folgenden Zeilen:

   ```yaml
     deploy:
   ...
       SEARCH_CONFIGURATION:
         engine: opensearch
   ```

1. Wenn Sie diese Zeilen nicht haben, fügen Sie sie zum `.magento.env.yaml` -Datei.
1. Wenn diese Zeilen vorhanden sind, **Engine ändern** von *[!DNL opensearch]* nach *[!DNL livesearch]*.
1. Bestätigen Sie die Änderung und stellen Sie sie dann erneut bereit.

## Verwandtes Lesen

* [Installieren [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html) in unserem Live Search-Handbuch
