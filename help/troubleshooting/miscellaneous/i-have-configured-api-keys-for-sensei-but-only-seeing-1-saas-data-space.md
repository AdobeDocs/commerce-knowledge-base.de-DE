---
title: Ich habe API-Schlüssel für Sensei konfiguriert, sehe jedoch nur einen SaaS-Datenspeicher
description: Dieser Artikel bietet eine Lösung für Probleme, bei denen nach der Konfiguration der API-Schlüssel für Sensei nur ein SaaS-Datenspeicher angezeigt wird.
exl-id: e13041da-b122-4684-8287-42132931f47a
feature: REST, Saas, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Ich habe API-Schlüssel für Sensei konfiguriert, sehe jedoch nur einen SaaS-Datenspeicher

Dieser Artikel bietet eine Lösung für Probleme, bei denen nach der Konfiguration der API-Schlüssel für Sensei nur ein SaaS-Datenspeicher angezeigt wird.

## Betroffene Produkte und Versionen

* Adobe Commerce (alle Bereitstellungsmethoden): Alle Versionen
* Magento Open Source: Alle Versionen
* Erweiterung oder Technologie (Fastly, New Relic usw.), Adobe Sensei (Produkt Recommendations/Live Search)

## Problem

Ich habe die API-Schlüssel für Sensei konfiguriert, sehe jedoch nur einen SaaS-Datenspeicher.

## Ursache

Die Anzahl der angezeigten SaaS-Datenräume hängt von Ihrer Commerce-Lizenz ab:

* Adobe Commerce: ein Produktionsdatenbereich; zwei Testdatenbereiche
* Magento Open Source - Ein Produktionsdatenbereich; keine Testdatenbereiche

## Lösung

* Stellen Sie sicher, dass die API-Schlüssel für das Konto des Kontoinhabers erstellt wurden. Selbst wenn Sie gemeinsamen Zugriff auf ihr Konto erhalten und die Schlüssel in Ihrem eigenen Konto erstellt haben, wird Ihnen dies nicht mehr als einen Datenspeicher gewähren.
* Wenn die Schlüssel für das Konto des Kontoinhabers generiert wurden, stellen Sie sicher, dass die Lizenz aktiv ist, d. h. dass keine ausstehenden Rechnungen vorhanden sind.
