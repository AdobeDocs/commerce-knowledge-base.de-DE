---
title: Site aufgrund von Ursprungsverdeckung nicht zugänglich
description: Dieser Artikel bietet eine Lösung für den Fall, dass die Storefront und/oder der Admin Ihrer Adobe Commerce-Cloud-Infrastruktur bzw. Ihrer Staging- oder Produktions-Site nicht zugänglich ist.
exl-id: 4412d744-3066-4f78-bc45-8149614ce455
feature: Products
role: Developer
source-git-commit: b58e182c64b3fad508145d9078619ddbe0e2b887
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Site aufgrund von Ursprungsverdeckung nicht zugänglich

Dieser Artikel bietet eine Lösung für den Fall, dass die Storefront und/oder der Admin Ihrer Adobe Commerce-Cloud-Infrastruktur bzw. Ihrer Staging- oder Produktions-Site nicht zugänglich ist.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.3.x, 2.4.x

## Problem

https:&#x200B;//mydomain.com.c.&lt;projectid>.magento.cloud/ ist nicht mehr zugänglich.

<u>Schritte zur Reproduktion:</u>

1. Melden Sie sich bei Ihrem Projekt an.
1. Klicken Sie **Projekt aufrufen**, um eine Liste der URLs und SSH anzuzeigen.

<u>Tatsächliche Ergebnisse:</u>

Die Seite kann nicht geladen werden und es wird der folgende Fehler angezeigt:

*NET::ERR\_CERT\_INVALID* *TLS-Warnhinweis, ungültiges Zertifikat (554):*

<u>Erwartete Ergebnisse:</u>

Die Seite wurde geladen.

## Ursache

Das Verdecken des Ursprungs wurde aktiviert, sodass der Ursprung nicht mehr direkt zugänglich ist.

Origin Cloaking ist eine Sicherheitsfunktion, mit der Adobe Commerce jeden Nicht-Fastly-Traffic blockieren kann, der an die Cloud-Infrastruktur (Herkunft) geleitet wird, um DDoS-Angriffe zu verhindern.

## Lösung

* Wenn Ihre Cloud-Site live ist, wechseln Sie zu https://mydomain.com/.
* Wenn Sie eine aktive Website (nicht die Cloud) haben, richten Sie mithilfe der Domain https://mydomain.com/ eine Subdomain-`mcprod.mydomain.com` ein und aktualisieren Sie Ihre **Basis-URL** stattdessen auf *https://mcprod.mydomain.com*, dann [verweisen Sie den DNS auf Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#update-dns-configuration-with-development-settings).

## Verwandtes Lesen

* [Häufig gestellte Fragen zur Aktivierung der Ursprünglichen Cloaking](/help/faq/general/fastly-origin-cloaking-enablement-faq.md) in unserer Support-Wissensdatenbank
* [Checkliste zur Einrichtung einer neuen Domain](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/checklist-for-setting-up-a-new-domain) in unserer Support-Wissensdatenbank
