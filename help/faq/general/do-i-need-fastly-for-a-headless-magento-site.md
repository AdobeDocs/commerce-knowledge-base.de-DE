---
title: Benötige ich Fastly für eine Headless-Adobe Commerce-Site?
description: Benötige ich Fastly für eine Headless-Adobe Commerce-Site?
exl-id: d7e07160-6a61-4c03-8f8c-4f879d86ea44
feature: Cache, GraphQL, Compliance
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '319'
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
Siehe [Cloud für Adobe Commerce > Fastly](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/cdn/fastly) in unserer Entwicklerdokumentation.

Dennoch benötigen Sie wahrscheinlich Fastly, um sein SSL-Zertifikat verwenden zu können.

Alle Kunden von Adobe Commerce auf Cloud-Infrastrukturen erhalten im Rahmen des Cloud-Abonnementplans ein gemeinsames SSL-Zertifikat von Fastly. Das Hinzufügen eines eigenen SSL-Zertifikats zu Fastly ist eine separate und ziemlich teure kostenpflichtige Option. Daher empfehlen wir dringend, Fastly zu aktivieren und es zumindest in Staging- und Produktionsumgebungen zu testen, bevor es live geht - auch für Ihre Headless-Adobe Commerce-Website.

## Weitere Informationen

* [Headless-Websites: Was hat es mit der entkoppelten Architektur auf sich?](https://pantheon.io/blog/headless-websites-whats-big-deal-decoupled-architecture) von [Josh ](https://pantheon.io/team/josh-koenig).
* [Fastly](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/cdn/fastly) in unserer Entwicklerdokumentation.
