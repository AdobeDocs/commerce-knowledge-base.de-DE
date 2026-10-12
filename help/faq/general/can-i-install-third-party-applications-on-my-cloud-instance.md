---
title: Kann ich Anwendungen von Drittanbietern auf meiner Cloud-Instanz installieren?
description: Anzahl Die Installation von Drittanbieter-Apps (wie WordPress oder Drupal) auf dem Adobe Commerce auf Cloud-Infrastrukturservern ist nicht zulässig. Solche Anwendungen müssen auf externen Servern gehostet werden.
exl-id: 3abbe282-2a14-4597-8af8-da1edcbece30
feature: Cloud, Compliance, Install
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '278'
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

Um die Integration Ihrer Adobe Commerce in Cloud-Infrastrukturanwendungen mit auf externen Servern gehosteten Lösungen von Drittanbietern zu verbessern, empfehlen wir Ihnen, die [Commerce Marketplace](https://marketplace.magento.com)-Erweiterungen zu verwenden, die zu Ihrem Zweck passen.
