---
title: Umgehen von WAF für GraphQL-Anforderungen
description: In diesem Artikel wird erläutert, wie Sie WAF für GraphQL-Anforderungen umgehen.
feature: GraphQL
source-git-commit: c35d4ba82fbe1657756e160a73fd575c736b4e1c
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Umgehen von WAF für GraphQL-Anforderungen

In diesem Artikel wird erläutert, wie Sie WAF für GraphQL-Anforderungen umgehen, wenn die [!DNL Fastly] WAF blockiert Ihre GraphQL-Anfragen.

## Betroffene Produkte und Versionen

Adobe Commerce in der Cloud-Infrastruktur (alle Versionen)

## Ursache

Aufgrund der inhärenten Natur von GraphQL-Anforderungen kann es viele wiederholte Zeichen geben, die zu einem falsch positiven Blockieren der Anforderungen durch die [!DNL Fastly] WAF.

## Lösung

1. Umgehen Sie die WAF für diese Anforderungen, indem Sie ein benutzerdefiniertes Snippet über das [!DNL Fastly] Magento-Modul:

   Typ: neue Priorität: 15 Inhalt:

   ```
   if( req.url.path ~ "^/graphql" ) {
       set req.http.bypasswaf = "1";
   }
   ```

1. Klicken Sie auf **[!UICONTROL Upload VCL to Fastly]**.

## Verwandtes Lesen

* [Web Application Firewall (WAF)](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service) in Commerce im Handbuch zur Cloud-Infrastruktur.
* [Erste Schritte mit benutzerdefiniertem VCL](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets) in Commerce im Handbuch zur Cloud-Infrastruktur.

