---
title: Benötige ich Fastly für eine Headless-Adobe Commerce-Site?
description: Benötige ich Fastly für eine Headless-Adobe Commerce-Site?
exl-id: d7e07160-6a61-4c03-8f8c-4f879d86ea44
feature: Cache, GraphQL, Compliance
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%
---
# Benötige ich Fastly für eine Headless-Adobe Commerce-Site?

>[!NOTE]
>
>Alle Kunden müssen Fastly für ihre Produktions- und Staging-Umgebungen verwenden. Fastly ist ein Content Delivery Network (CDN), das im Rahmen Ihrer Adobe Commerce-Cloud-Infrastrukturprojekte vollständige Seitenzwischenspeicherung, Bildoptimierung und Sicherheitsdienste (DDoS und WAF) bereitstellt. Dies sind Kernkomponenten der Adobe Commerce-Lösung, die mehr Leistung und Sicherheit bieten. Diese Funktionen sind Teil der PCI-Compliance von Adobe. Sie müssen diese Fastly Services in Ihren Starter Master-, Staging-, Pro Staging- und Produktionsumgebungen einrichten. Wenn Sie Adobe Commerce in einer Headless-Bereitstellung verwenden, muss der gesamte API-Traffic aus dem öffentlichen Internet über Fastly laufen. Wir empfehlen dringend, Fastly zu verwenden, um GraphQL-Antworten zwischenzuspeichern. Siehe [GraphQL-Entwicklerhandbuch > Caching mit Fastly](https://developer.adobe.com/commerce/webapi/graphql/usage/caching/#caching-with-fastly) in unserer Entwicklerdokumentation.

## **Frage**

Ich entwickle eine Headless-Implementierung von Adobe Commerce. Muss ich Fastly weiterhin als CDN-Service dafür verwenden?

## **Antwort**

Nein, tust du nicht. In dieser Situation können Sie die Verwendung von Fastly überspringen - zumindest zu Beginn der Entwicklung.

Die einzige Situation, die Sie möglicherweise nicht aktivieren möchten, ist für eine Headless-Bereitstellung.
Siehe [Cloud für Adobe Commerce > Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly) in unserer Entwicklerdokumentation.

Dennoch benötigen Sie wahrscheinlich Fastly, um sein SSL-Zertifikat verwenden zu können.

Alle Kunden von Adobe Commerce auf Cloud-Infrastrukturen erhalten im Rahmen des Cloud-Abonnementplans ein gemeinsames SSL-Zertifikat von Fastly. Das Hinzufügen eines eigenen SSL-Zertifikats zu Fastly ist eine separate und ziemlich teure kostenpflichtige Option. Daher empfehlen wir dringend, Fastly zu aktivieren und es zumindest in Staging- und Produktionsumgebungen zu testen, bevor es live geht - auch für Ihre Headless-Adobe Commerce-Website.

## Weitere Informationen

* [Headless-Websites: Was ist das Besondere an der entkoppelten Architektur?](https://pantheon.io/blog/headless-websites-whats-big-deal-decoupled-architecture) von [Josh &#x200B;](https://pantheon.io/team/josh-koenig).
* [Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly) in unserer Entwicklerdokumentation.
