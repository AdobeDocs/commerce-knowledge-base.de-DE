---
title: Kann ich Anwendungen von Drittanbietern auf meiner Cloud-Instanz installieren?
description: Anzahl Die Installation von Drittanbieter-Apps (wie WordPress oder Drupal) auf dem Adobe Commerce auf Cloud-Infrastrukturservern ist nicht zulässig. Solche Anwendungen müssen auf externen Servern gehostet werden.
exl-id: 3abbe282-2a14-4597-8af8-da1edcbece30
feature: Cloud, Compliance, Install
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Kann ich Anwendungen von Drittanbietern auf meiner Cloud-Instanz installieren?

Anzahl Die Installation von Drittanbieter-Apps (wie WordPress oder Drupal) auf dem Adobe Commerce auf Cloud-Infrastrukturservern ist nicht zulässig. Solche Anwendungen müssen auf externen Servern gehostet werden.

## Gründe

### Vereinbarung über die Nutzungsbedingungen

In Artikel 18 der Adobe Commerce [&#x200B; Cloud Infrastructure Edition (](https://magento.com/legal/terms/cloud-terms)) heißt es:

> Der Kunde erklärt sich damit einverstanden, dass Adobe Commerce und der Service nicht zum Hosten anderer Software-Anwendungen von Drittanbietern verwendet werden, die nicht direkt von der Software abhängig sind.

Als Cloud-Lösung übernimmt Adobe die volle Verantwortung für die Sicherheit Ihres Servers. Um hohe Sicherheit zu gewährleisten, erlauben wir nur das Hosten der Adobe Commerce-Anwendung auf dem dedizierten Cloud-Server.

### PCI-Compliance

Als PCI-zertifizierter Lösungsanbieter der Stufe 1 muss Adobe Commerce in der Cloud-Infrastruktur den PCI-Datensicherheitsstandard einhalten und Folgendes sicherstellen:

>… Entwicklung und Wartung sicherer Systeme und Anwendungen
> ([Adobe-Ansatz für PCI-Compliance](https://magento.com/pci-compliance) Anforderung 6, Aufrechterhaltung eines Programms zur Schwachstellenverwaltung)

Da Adobe die PCI-Konformität von Anwendungen von Drittanbietern nicht gewährleisten kann, ist die Installation solcher Apps auf Cloud-Servern nicht zulässig.

## Hinweis: Verwenden Sie Commerce Marketplace-Erweiterungen für bessere Integrationen.

Um die Integration Ihrer Adobe Commerce in Cloud-Infrastrukturanwendungen mit auf externen Servern gehosteten Lösungen von Drittanbietern zu verbessern, empfehlen wir Ihnen, die [Commerce Marketplace](https://marketplace.magento.com)-Erweiterungen zu verwenden, die zu Ihrem Zweck geeignet sind.
