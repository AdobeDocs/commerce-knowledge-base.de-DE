---
title: Geplante Staging-Aktualisierungen von Inhalten werden nicht mit veraltetem Fastly-Cache angezeigt
description: Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass Adobe Commerce-Stores bei Verwendung von Content Staging und Fastly keine geplanten Aktualisierungen anzeigen. Das Problem ist auf die standardmäßig aktivierte Fastly-Soft-Bereinigung zurückzuführen. Diese Funktion reduziert die Last der Anwendungsressourcen und generiert nur bei einer zweiten Anfrage einen neuen Cache. Um dieses Problem zu beheben, können Sie über den Commerce-Administrator die Option CMS-Seite bereinigen aktivieren, um immer neue Inhalte zu generieren und bereitzustellen.
exl-id: becbffaa-b6dd-4e9b-894e-17901c40223a
feature: CMS, Cache, Page Content, Staging
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '454'
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
