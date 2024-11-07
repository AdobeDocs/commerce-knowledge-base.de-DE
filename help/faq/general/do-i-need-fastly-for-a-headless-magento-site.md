---
title: Benötige ich eine schnelle Website für eine Headless Adobe Commerce-Site?
description: Benötige ich eine schnelle Website für eine Headless Adobe Commerce-Site?
exl-id: d7e07160-6a61-4c03-8f8c-4f879d86ea44
feature: Cache, GraphQL, Compliance
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Benötige ich eine schnelle Website für eine Headless Adobe Commerce-Site?

>[!NOTE]
>
>Alle Kunden müssen Fastly für ihre Produktions- und Staging-Umgebungen verwenden. Fastly ist ein Content Delivery Network (CDN), das als Teil Ihres Adobe Commerce für Cloud-Infrastrukturprojekte vollständige Seitenzwischenspeicherung, Bildoptimierung und Sicherheitsdienste (DoS und WAF) bereitstellt. Dies sind Kernkomponenten der Adobe Commerce-Lösung, die eine höhere Leistung und Sicherheit bieten. Diese Funktionen sind Teil der PCI Compliance von Adobe. Sie müssen diese Schnelldienste in Ihren Starter Master-, Staging-, Pro Staging- und Produktionsumgebungen einrichten. Wenn Sie Adobe Commerce in einer Headless-Implementierung verwenden, muss der gesamte API-Traffic aus dem öffentlichen Internet schnell übertragen werden. Wir empfehlen dringend, die Funktion &quot;Schnell&quot;zu verwenden, um GraphQL-Antworten zwischenzuspeichern. Siehe [GraphQL-Entwicklerhandbuch > Zwischenspeicherung mit Fastly](https://developer.adobe.com/commerce/webapi/graphql/usage/caching/#caching-with-fastly) in unserer Entwicklerdokumentation.

## **Frage**

Ich arbeite derzeit an einer Headless-Implementierung von Adobe Commerce. Muss ich noch Fastly als CDN-Dienst verwenden?

## **Antwort**

Nein, nicht. In diesem Fall können Sie die Verwendung von Fastly überspringen - zumindest zu Beginn der Entwicklung.

Die einzige Situation, die Sie möglicherweise nicht aktivieren möchten, ist eine Headless-Implementierung.
Siehe [Cloud für Adobe Commerce > Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly) in unserer Entwicklerdokumentation.

Wahrscheinlich benötigen Sie jedoch Fastly für die Verwendung seines SSL-Zertifikats.

Alle Adobe Commerce-Kunden mit Cloud-Infrastruktur erhalten im Rahmen des Cloud-Abonnementplans von Fastly ein freigegebenes SSL-Zertifikat. Das Hinzufügen eines eigenen SSL-Zertifikats zu Fastly ist eine separate und ziemlich teure gebührenpflichtige Option. Daher empfehlen wir dringend, Fastly zu aktivieren und diese zumindest in Staging- und Produktionsumgebungen zu testen, bevor sie live geschaltet werden - auch für Ihre Headless Adobe Commerce-Website.

## Weitere Informationen

* [Headless-Websites: Was ist der große Deal mit entkoppelter Architektur?](https://pantheon.io/blog/headless-websites-whats-big-deal-decoupled-architecture) von [Josh König](https://pantheon.io/team/josh-koenig).
* [Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly) in unserer Entwicklerdokumentation.
