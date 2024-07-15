---
title: Site aufgrund der Ursprungsverdeckung nicht zugänglich
description: Dieser Artikel bietet eine Lösung für den Fall, dass der Zugriff auf Ihre Adobe Commerce in der Staging- oder Produktions-Site-Storefront und/oder -Admin-Umgebung nicht möglich ist.
exl-id: 4412d744-3066-4f78-bc45-8149614ce455
feature: Products
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---

# Site aufgrund der Ursprungsverdeckung nicht zugänglich

Dieser Artikel bietet eine Lösung für den Fall, dass der Zugriff auf Ihre Adobe Commerce in der Staging- oder Produktions-Site-Storefront und/oder -Admin-Umgebung nicht möglich ist.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.3.x, 2.4.x

## Problem

https: &#x200B;//mydomain.com.c.&lt;projektid>.magento.cloud/ ist nicht mehr verfügbar.

<u>Zu reproduzierende Schritte:</u>

1. Melden Sie sich bei Ihrem Projekt an.
1. Klicken Sie auf **Projekt aufrufen** , um eine Liste der URLs und SSH anzuzeigen.

<u>Tatsächliche Ergebnisse:</u>

Seite kann mit dem folgenden Fehler nicht geladen werden:

*NET::ERR\_CERT\_INVALID* *TLS-Warnhinweis, ungültiges Zertifikat (554):*

<u>Erwartete Ergebnisse:</u>

Seite wurde erfolgreich geladen.

## Ursache

Die Origin Cloaking wurde aktiviert, sodass der Ursprung nicht mehr direkt zugänglich ist.

Die Herkunftsverdeckung ist eine Sicherheitsfunktion, mit der Adobe Commerce jeglichen nicht schnellen Traffic, der zur Cloud-Infrastruktur (Ursprung) geleitet wird, blockieren kann, um DDoS-Angriffe zu verhindern.

## Lösung

* Wenn Ihre Cloud-Site live ist, wechseln Sie zu https://mydomain.com/.
* Wenn Sie über eine aktive Site (nicht Cloud) verfügen, richten Sie mithilfe der Domäne &quot;https://mydomain.com/&quot;die Unterdomäne &quot;`mcprod.mydomain.com`&quot;ein und aktualisieren Sie Ihre **Basis-URL** stattdessen auf &quot;*https://mcprod.mydomain.com*&quot;. Anschließend verweisen [auf Fastly](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#update-dns-configuration-with-development-settings).

## Verwandtes Lesen

[Häufig gestellte Fragen zur Aktivierung der frühzeitigen Ursprungsverschlüsselung](/help/faq/general/fastly-origin-cloaking-enablement-faq.md) in unserer Support-Wissensdatenbank.
