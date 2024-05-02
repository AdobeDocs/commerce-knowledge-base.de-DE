---
title: Ich habe API-Schlüssel für Sensei konfiguriert, sehe aber nur einen SaaS-Datenspeicher
description: Dieser Artikel bietet eine Lösung für Probleme, bei denen nach der Konfiguration der API-Schlüssel für Sensei nur ein SaaS-Datenraum angezeigt wird.
exl-id: e13041da-b122-4684-8287-42132931f47a
feature: REST, Saas, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Ich habe API-Schlüssel für Sensei konfiguriert, sehe aber nur einen SaaS-Datenspeicher

Dieser Artikel bietet eine Lösung für Probleme, bei denen nach der Konfiguration der API-Schlüssel für Sensei nur ein SaaS-Datenraum angezeigt wird.

## Betroffene Produkte und Versionen

* Adobe Commerce (alle Bereitstellungsmethoden): alle Versionen
* Magento Open Source: alle Versionen
* Erweiterung oder Technologie (schnell, New Relic usw.), Adobe Sensei (Product Recommendations/Live Search)

## Problem

Ich habe die API-Schlüssel für Sensei konfiguriert, sehe aber nur einen SaaS-Datenraum.

## Ursache

Die Anzahl der angezeigten SaaS-Datenräume hängt von Ihrer Commerce-Lizenz ab:

* Adobe Commerce - Ein Produktionsdatenraum; zwei Testdatenbereiche
* Magento Open Source - Ein Produktionsdatenraum; keine Testdatenbereiche

## Lösung

* Stellen Sie sicher, dass die API-Schlüssel im Konto des Kontoinhabers erstellt wurden. Selbst wenn Ihnen freigegebener Zugriff auf Ihr Konto gewährt und die Schlüssel auf Ihrem eigenen Konto erstellt wurden, erhalten Sie dadurch nicht mehr als einen Datenspeicherplatz.
* Wenn die Schlüssel auf dem Konto des Kontoinhabers generiert wurden, stellen Sie sicher, dass die Lizenz aktiv ist, d. h. keine ausstehenden Rechnungen vorliegen.
