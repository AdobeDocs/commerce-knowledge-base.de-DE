---
title: ' [!DNL opensearch] -Suchmaschine existiert nicht. Zurückfallen auf [!DNL livesearch].'
description: Dieser Artikel bietet eine Lösung für das Problem, bei dem Sie den Fehler " [!DNL opensearch] -Suchmaschine existiert nicht“ sehen. Zurückgreifen auf " [!DNL livesearch].“ in Adobe Commerce auf Cloud-Infrastruktur.
feature: Deploy, Search
role: Developer
exl-id: a6cc981d-b8f0-402d-8771-60d2f21f09f8
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---

# Fehler [!DNL opensearch] Suchmaschine existiert nicht. Zurückfallen auf [!DNL livesearch].

Dieser Artikel bietet eine Lösung für das Problem, bei dem der folgende Fehler angezeigt wird *(Fehler: [!DNL opensearch] Suchmaschine existiert nicht. Zurückfallen auf [!DNL livesearch].* in Adobe Commerce auf der Cloud-Infrastruktur, in der [!DNL Live Search] verwendet wird.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, alle Versionen
* [!DNL Live Search] ist installiert und wird verwendet

## Problem

Die folgende Meldung wird in den Protokollen angezeigt (und ist in [!DNL New Relic] zu beobachten):
*Fehler: [!DNL opensearch] Suchmaschine existiert nicht. Zurückfallen auf [!DNL livesearch].*

## Lösung

1. Ändern Sie die `.magento.env.yaml`.
1. Suchen Sie die folgenden Zeilen:

   ```yaml
     deploy:
   ...
       SEARCH_CONFIGURATION:
         engine: opensearch
   ```

1. Wenn Sie diese Zeilen nicht haben, fügen Sie sie zur `.magento.env.yaml` hinzu.
1. Wenn diese Zeilen vorhanden sind, **ändern Sie die Engine** von *[!DNL opensearch]* auf *[!DNL livesearch]*.
1. Bestätigen Sie die Änderung und stellen Sie sie dann erneut bereit.

## Verwandtes Lesen

* [Installieren [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html) in unserem Live Search-Handbuch
