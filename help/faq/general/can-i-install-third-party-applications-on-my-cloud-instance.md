---
title: Kann ich Anwendungen von Drittanbietern auf meiner Cloud-Instanz installieren?
description: Anzahl Die Installation von Drittanbieteranwendungen (wie WordPress oder Drupal) auf Adobe Commerce auf Cloud-Infrastrukturservern ist nicht zulässig. Sie müssen solche Anwendungen auf externen Servern hosten.
exl-id: 3abbe282-2a14-4597-8af8-da1edcbece30
feature: Cloud, Compliance, Install
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Kann ich Anwendungen von Drittanbietern auf meiner Cloud-Instanz installieren?

Anzahl Die Installation von Drittanbieteranwendungen (wie WordPress oder Drupal) auf Adobe Commerce auf Cloud-Infrastrukturservern ist nicht zulässig. Sie müssen solche Anwendungen auf externen Servern hosten.

## Gründe

### Vereinbarung über die Nutzungsbedingungen

In Artikel 18 der Adobe Commerce on Cloud Infrastructure Edition [Vereinbarung über die Nutzungsbedingungen](https://magento.com/legal/terms/cloud-terms) heißt es:

> Der Kunde erklärt sich damit einverstanden, dass Adobe Commerce und der Service nicht zum Hosten anderer Softwareanwendungen von Drittanbietern verwendet werden, die nicht direkt von der Software abhängig sind.

Als Cloud-Lösung übernimmt Adobe die volle Verantwortung für die Sicherheit Ihres Servers. Um hohe Sicherheit zu gewährleisten, ist es nur zulässig, die Adobe Commerce-Anwendung auf dem dedizierten Cloud-Server zu hosten.

### PCI-Compliance

Als PCI-zertifizierter Lösungsanbieter der Stufe 1 muss Adobe Commerce in der Cloud-Infrastruktur dem PCI Data Security Standard entsprechen und sicherstellen, dass:

>... Entwicklung und Pflege sicherer Systeme und Anwendungen
> ([Adobe-Ansatz für PCI Compliance](https://magento.com/pci-compliance) Anforderung 6, Pflege eines Programms zur Verwaltung von Sicherheitsrisiken)

Da Adobe die PCI-Compliance von Drittanbieteranwendungen nicht garantieren kann, ist die Installation solcher Apps auf Cloud-Servern nicht zulässig.

## Hinweis: Verwenden von Commerce Marketplace-Erweiterungen für bessere Integrationen

Um die Integration Ihrer Adobe Commerce in die Cloud-Infrastrukturanwendung mit den Drittanbieterlösungen zu verbessern, die auf externen Servern gehostet werden, empfehlen wir Ihnen, die [Commerce Marketplace](https://marketplace.magento.com) -Erweiterungen zu verwenden, die Ihren Anforderungen entsprechen könnten.
