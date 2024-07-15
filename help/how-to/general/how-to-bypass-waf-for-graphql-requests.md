---
title: Umgehen von WAF für GraphQL-Anforderungen
description: In diesem Artikel wird erläutert, wie Sie WAF für GraphQL-Anforderungen umgehen.
feature: GraphQL
exl-id: 3a0f2c22-f976-4596-b6a9-4634be1ea4c3
source-git-commit: 2bec86818336a9ef4d8316e257a0ca4256cdd93c
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Umgehen von WAF für GraphQL-Anforderungen

In diesem Artikel wird erläutert, wie Sie WAF für GraphQL-Anforderungen umgehen, wenn die [!DNL Fastly]-WAF Ihre GraphQL-Anforderungen blockiert.

## Betroffene Produkte und Versionen

Adobe Commerce in der Cloud-Infrastruktur (alle Versionen)

## Ursache

Aufgrund der inhärenten Natur von GraphQL-Anforderungen kann es viele wiederholte Zeichen geben, die eine fälschlich positive Blockierung der Anforderungen durch die [!DNL Fastly]-WAF Trigger haben können.

## Lösung

1. Umgehen Sie die WAF für diese Anforderungen, indem Sie ein benutzerdefiniertes Snippet über das Magento-Modul [!DNL Fastly] hinzufügen:

   Typ: recv
Priorität: 15
content:

   ```
   if( req.url.path ~ "^/graphql" ) {
       set req.http.bypasswaf = "1";
   }
   ```

1. Klicken Sie auf **[!UICONTROL Upload VCL to Fastly]**.

## Verwandtes Lesen

* [Web Application Firewall (WAF)](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service) im Handbuch zu Commerce on Cloud Infrastructure.
* [Erste Schritte mit benutzerdefiniertem VCL](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets) im Handbuch zu Commerce on Cloud Infrastructure.
