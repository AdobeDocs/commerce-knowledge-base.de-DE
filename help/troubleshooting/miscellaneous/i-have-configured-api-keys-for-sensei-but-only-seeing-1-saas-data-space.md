---
title: Ich habe API-Schlüssel für die Adobe-KI konfiguriert, sehe jedoch nur einen SaaS-Datenspeicher
description: Dieser Artikel bietet eine Lösung für Probleme, bei denen nach der Konfiguration der API-Schlüssel für die Adobe-KI nur ein SaaS-Datenspeicher angezeigt wird.
exl-id: e13041da-b122-4684-8287-42132931f47a
feature: REST, Saas, Observability
role: Developer
source-git-commit: 27b0836380c3040b26076b9cb81b9328cb2c9ff2
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Ich habe API-Schlüssel für die Adobe-KI konfiguriert, sehe jedoch nur einen SaaS-Datenspeicher

Dieser Artikel bietet eine Lösung für Probleme, bei denen nach der Konfiguration der API-Schlüssel für die Adobe-KI nur ein SaaS-Datenspeicher angezeigt wird.

## Betroffene Produkte und Versionen

* Adobe Commerce (alle Bereitstellungsmethoden): Alle Versionen
* Magento Open Source: alle Versionen
* Erweiterung oder Technologie (Fastly, New Relic usw.), Adobe AI (Product Recommendations/Live Search)

## Problem

Ich habe die API-Schlüssel für die Adobe-KI konfiguriert, sehe jedoch nur einen SaaS-Datenspeicher.

## Ursache

Die Anzahl der angezeigten SaaS-Datenräume hängt von Ihrer Commerce-Lizenz ab:

* Adobe Commerce: ein Produktionsdatenbereich; zwei Testdatenbereiche
* Magento Open Source - Ein Produktionsdatenbereich; keine Testdatenbereiche

## Lösung

* Stellen Sie sicher, dass die API-Schlüssel für das Konto des Kontoinhabers erstellt wurden. Selbst wenn Sie gemeinsamen Zugriff auf ihr Konto erhalten und die Schlüssel in Ihrem eigenen Konto erstellt haben, wird Ihnen dies nicht mehr als einen Datenspeicher gewähren.
* Wenn die Schlüssel für das Konto des Kontoinhabers generiert wurden, stellen Sie sicher, dass die Lizenz aktiv ist, d. h. dass keine ausstehenden Rechnungen vorhanden sind.
