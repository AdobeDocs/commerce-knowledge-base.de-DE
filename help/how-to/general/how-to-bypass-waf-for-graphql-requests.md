---
title: Umgehen von WAF für GraphQL-Anfragen
description: In diesem Artikel wird erläutert, wie Sie WAF für GraphQL-Anfragen umgehen.
feature: GraphQL
exl-id: 3a0f2c22-f976-4596-b6a9-4634be1ea4c3
source-git-commit: 2bec86818336a9ef4d8316e257a0ca4256cdd93c
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Umgehen von WAF für GraphQL-Anfragen

In diesem Artikel wird erläutert, wie Sie WAF für GraphQL-Anfragen umgehen können, wenn die [!DNL Fastly] WAF Ihre GraphQL-Anfragen blockiert.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur (alle Versionen)

## Ursache

Aufgrund der inhärenten Natur von GraphQL-Anfragen kann es eine Vielzahl von wiederholten Zeichen geben, die einen Trigger zu falsch positiven Blockierungen der Anfragen durch die [!DNL Fastly] WAF darstellen können.

## Lösung

1. Umgehen Sie die WAF für diese Anfragen, indem Sie ein benutzerdefiniertes Snippet über das [!DNL Fastly] Magento-Modul hinzufügen:

   Typ: recv
Priorität: 15
Inhalt:

   ```
   if( req.url.path ~ "^/graphql" ) {
       set req.http.bypasswaf = "1";
   }
   ```

1. Klicken Sie auf **[!UICONTROL Upload VCL to Fastly]**.

## Verwandtes Lesen

* [Web Application Firewall (WAF)](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service) Handbuch in Commerce on Cloud Infrastructure.
* [Erste Schritte mit benutzerdefiniertem VCL](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets) in Commerce im Handbuch zur Cloud-Infrastruktur.
