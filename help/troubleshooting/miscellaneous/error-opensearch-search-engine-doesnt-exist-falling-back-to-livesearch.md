---
title: Fehler [!DNL opensearch] Suchmaschine ist nicht vorhanden. Falling zurück zu [!DNL livesearch].
description: Dieser Artikel bietet eine Lösung für das Problem, bei dem der Fehler "Error- [!DNL opensearch] search engine not exists"angezeigt wird. Falling back zu [!DNL livesearch]."in Adobe Commerce in der Cloud-Infrastruktur.
feature: Deploy, Search
role: Developer
exl-id: a6cc981d-b8f0-402d-8771-60d2f21f09f8
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---

# Fehler [!DNL opensearch] Suchmaschine ist nicht vorhanden. Falling zurück zu [!DNL livesearch].

Dieser Artikel bietet eine Lösung für das Problem, bei dem der Fehler angezeigt wird: *Fehler: [!DNL opensearch] Suchmaschine ist nicht vorhanden. Falling zurück zu [!DNL livesearch].* in Adobe Commerce in der Cloud-Infrastruktur, in der [!DNL Live Search] verwendet wird.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle Versionen
* [!DNL Live Search] wird installiert und in Verwendung

## Problem

Die folgende Meldung wird in den Protokollen angezeigt (und in [!DNL New Relic] sichtbar):
*Fehler: [!DNL opensearch] Suchmaschine existiert nicht. Zurückfallen auf [!DNL livesearch].*

## Lösung

1. Ändern Sie die Datei &quot;`.magento.env.yaml`&quot;.
1. Suchen Sie die folgenden Zeilen:

   ```yaml
     deploy:
   ...
       SEARCH_CONFIGURATION:
         engine: opensearch
   ```

1. Wenn Sie diese Zeilen nicht haben, fügen Sie sie der Datei `.magento.env.yaml` hinzu.
1. Wenn diese Zeilen vorhanden sind, ändert **die Engine** von *[!DNL opensearch]* in *[!DNL livesearch]*.
1. Bestätigen Sie die Änderung und stellen Sie sie dann erneut bereit.

## Verwandtes Lesen

* [Installieren [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html) in unserem Live-Suchleitfaden
