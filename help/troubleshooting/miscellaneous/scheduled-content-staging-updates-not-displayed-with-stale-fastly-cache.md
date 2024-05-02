---
title: Aktualisierungen des Staging für geplante Inhalte werden nicht mit veraltetem Fastly-Cache angezeigt
description: Dieser Artikel enthält eine Fehlerbehebung für Fälle, in denen Adobe Commerce Stores bei der Verwendung von Content Staging und Fastly keine geplanten Aktualisierungen anzeigen. Das Problem ist auf die standardmäßig aktivierte Fastly Soft Purge zurückzuführen. Diese Funktion reduziert das Laden der Anwendungsressourcen und generiert nur bei einer zweiten Anforderung einen neuen Cache. Um dieses Problem zu beheben, können Sie die Option CMS-Seite bereinigen über den Commerce-Administrator aktivieren, um immer neue Inhalte zu generieren und bereitzustellen.
exl-id: becbffaa-b6dd-4e9b-894e-17901c40223a
feature: CMS, Cache, Page Content, Staging
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# Aktualisierungen des Staging für geplante Inhalte werden nicht mit veraltetem Fastly-Cache angezeigt

Dieser Artikel enthält eine Fehlerbehebung für Fälle, in denen Adobe Commerce Stores bei der Verwendung von Content Staging und Fastly keine geplanten Aktualisierungen anzeigen. Das Problem ist auf die standardmäßig aktivierte Fastly Soft Purge zurückzuführen. Diese Funktion reduziert das Laden der Anwendungsressourcen und generiert nur bei einer zweiten Anforderung einen neuen Cache. Um dieses Problem zu beheben, können Sie die Option CMS-Seite bereinigen über den Commerce-Administrator aktivieren, um immer neue Inhalte zu generieren und bereitzustellen.

## Problem

Geplante Aktualisierungen für ein Store-Inhalts-Asset (Seite, Produkt, Block usw.) werden nicht unmittelbar nach dem Startzeitpunkt der Aktualisierung auf der Storefront angezeigt. Dies geschieht, wenn Aktualisierungen mit der Variablen [Inhaltstaging](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html) Funktionalität.

## Ursache

Aufgrund der (standardmäßig aktivierten) Softbereinigungsfunktion von Fastly erhält die Adobe Commerce-Storefront beim Senden weiterhin den alten (veralteten) zwischengespeicherten Inhalt **der erste** Anfrage für das aktualisierte Asset an Fastly. Eine zweite Anforderung zur erneuten Generierung der Site-Daten ist erforderlich.

Daher kann Fastly veraltete Inhalte bis zur zweiten Anfrage für den aktualisierten Inhalt bereitstellen.

**Erwartete Zwischenspeicherung:** Nachdem wir ein Update für ein Inhalts-Asset mit Content Staging planen, sendet Adobe Commerce eine Anfrage zur Aktualisierung des Caches an Fastly. Aktualisiert den vorherigen zwischengespeicherten Inhalt schnell (ohne Inhalt zu löschen) und beginnt mit der Bereitstellung des aktualisierten Inhalts.

**Tatsächliche Zwischenspeicherung:** Wenn Fastly weiterhin den veralteten Inhalt beim Empfang bereitstellt **der erste** Anforderung des aktualisierten Inhalts, wird der Inhalt nur nach Erhalt neu generiert und korrigiert **der zweite** -Anfrage. Dieses Verhalten wurde implementiert, um die Server-Last zu reduzieren, indem der Cache nur in Bereichen mit nachweislichem Traffic erneuert wird, ohne den Cache für die gesamte Website neu zu generieren. Aktualisiert den Cache schnell und speichert die Anwendungsressourcen.

## Lösung

Wenn die Bereitstellung von veraltetem Inhalt auch für die erste Anforderung inakzeptabel ist, können Sie die Softbounce-Bereinigung deaktivieren und die Option CMS-Seite bereinigen aktivieren:

1. Melden Sie sich bei Ihrem lokalen Commerce-Administrator als Administrator an.
1. Navigieren Sie zu **Stores** > **Konfiguration** > **Erweitert** > **System** > **Vollständiger Seiten-Cache**.
1. Erweitern **Schnelle Konfiguration**, dann erweitern **Erweitert**.
1. Satz **Verwenden der weichen Bereinigung** nach *Nein*.
1. Satz **CMS-Seite bereinigen** nach *Ja*.
1. Klicks **Konfiguration speichern** oben auf der Seite.


![purge_options.png](assets/purge_options.png)

## Verwandte Dokumentation

* [Bereinigungsoptionen konfigurieren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) im Commerce on Cloud Infrastructure Guide.
* [Inhaltstaging](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html) in der Dokumentation zu Inhalt und Design.
* [Bereitstellen veralteter Inhalte](https://docs.fastly.com/guides/performance-tuning/serving-stale-content) in der Fastly-Dokumentation.
