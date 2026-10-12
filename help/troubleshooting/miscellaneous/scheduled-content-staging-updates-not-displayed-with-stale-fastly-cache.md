---
title: Geplante Staging-Aktualisierungen von Inhalten werden nicht mit veraltetem Fastly-Cache angezeigt
description: Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass Adobe Commerce-Stores bei Verwendung von Content Staging und Fastly keine geplanten Aktualisierungen anzeigen. Das Problem ist auf die standardmäßig aktivierte Fastly-Soft-Bereinigung zurückzuführen. Diese Funktion reduziert die Last der Anwendungsressourcen und generiert nur bei einer zweiten Anfrage einen neuen Cache. Um dieses Problem zu beheben, können Sie über den Commerce-Administrator die Option CMS-Seite bereinigen aktivieren, um immer neue Inhalte zu generieren und bereitzustellen.
exl-id: becbffaa-b6dd-4e9b-894e-17901c40223a
feature: CMS, Cache, Page Content, Staging
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: ddbd0f6e-b569-5a04-8a70-55058777c373
    internal-label: CMS
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: 0054e3a7-7067-583b-bfd2-ab39dada9ab5
    internal-label: Staging
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%
---
# Geplante Staging-Aktualisierungen von Inhalten werden nicht mit veraltetem Fastly-Cache angezeigt

Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass Adobe Commerce-Stores bei Verwendung von Content Staging und Fastly keine geplanten Aktualisierungen anzeigen. Das Problem ist auf die standardmäßig aktivierte Fastly-Soft-Bereinigung zurückzuführen. Diese Funktion reduziert die Last der Anwendungsressourcen und generiert nur bei einer zweiten Anfrage einen neuen Cache. Um dieses Problem zu beheben, können Sie über den Commerce-Administrator die Option CMS-Seite bereinigen aktivieren, um immer neue Inhalte zu generieren und bereitzustellen.

## Problem

Geplante Aktualisierungen für ein Store-Content-Asset (Seite, Produkt, Block usw.) werden nicht sofort nach dem Start der Aktualisierung in der Storefront angezeigt. Dies geschieht, wenn Aktualisierungen mithilfe der Funktion [Inhalts-Staging](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html) geplant wurden.

## Ursache

Aufgrund der (standardmäßig aktivierten) Soft Purge-Funktion von Fastly erhält die Adobe Commerce-Storefront beim Senden der ersten Anfrage **das aktualisierte Asset an Fastly weiterhin** alten (veralteten) zwischengespeicherten Inhalt. Fastly erfordert eine zweite Anfrage, um die Site-Daten neu zu generieren.

Infolgedessen kann Fastly veraltete Inhalte bis zur zweiten Anforderung für die aktualisierten Inhalte bereitstellen.

**Erwartetes Caching:** Nachdem wir eine Aktualisierung für ein Content-Asset mithilfe von Content-Staging geplant haben, sendet Adobe Commerce eine Anfrage zur Aktualisierung des Caches an Fastly. Invalidiert den vorherigen zwischengespeicherten Inhalt (ohne den Inhalt zu löschen) und beginnt mit der Bereitstellung des aktualisierten Inhalts.

**Tatsächliches Caching:** Wenn Fastly beim Empfang der **ersten** Anfrage für den aktualisierten Inhalt weiterhin den veralteten Inhalt bereitstellt, sendet es nur nach Erhalt **zweiten** Anfrage neu generierten, korrekten Inhalt. Dieses Verhalten wurde implementiert, um die Server-Last zu reduzieren, indem der Cache nur in Bereichen mit nachgewiesenem Traffic erneuert wurde, ohne den Cache für die gesamte Website neu zu generieren. Aktualisiert den Cache schnell und speichert so die Anwendungsressourcen.

## Lösung

Wenn die Bereitstellung veralteter Inhalte selbst für die erste Anfrage inakzeptabel ist, können Sie die Soft Purge-Funktion deaktivieren und die CMS-Seite „Bereinigen“ aktivieren:

1. Melden Sie sich bei Ihrem lokalen Commerce-Administrator als Administrator an.
1. Navigieren Sie **Stores** > **Konfiguration** > **Erweitert** > **System** > **Vollständiger Seitencache**.
1. Erweitern Sie **Fastly Configuration** und erweitern Sie dann **Advanced**.
1. Legen **Verwenden Sie Soft Purge** auf *Nein* fest.
1. Legen Sie **CMS-Seite bereinigen** auf *Ja* fest.
1. Klicken **oben auf** Seite auf „Konfiguration speichern“.


![purge_options.png](assets/purge_options.png)

## Verwandte Dokumentation

* [Bereinigungsoptionen konfigurieren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) im Handbuch Commerce on Cloud Infrastructure .
* [Inhalts-Staging](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html) in der Dokumentation zu Inhalt und Design.
* [Serving Stale Content](https://docs.fastly.com/guides/performance-tuning/serving-stale-content) in der Fastly-Dokumentation.
