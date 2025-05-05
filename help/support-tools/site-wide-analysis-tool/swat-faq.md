---
title: Häufig gestellte  [!DNL Site-Wide Analysis Tool]  zu Adobe Commerce-Berichten
description: Erfahren Sie mehr über  [!DNL Site-Wide Analysis Tool], ein proaktives Self-Service-Tool und ein zentrales Repository, das detaillierte Systemeinblicke und Empfehlungen bietet, um die Sicherheit und Bedienbarkeit Ihrer Adobe Commerce-Installation zu gewährleisten.
exl-id: 7c843d55-9e2c-4b18-8859-0ebad0ae28cf
feature: Best Practices, Saas, Support, Tools and External Services
role: Admin
source-git-commit: 580ad148cd4346868cd9892a1ae9a4d85f73edce
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Häufig gestellte Fragen zum Adobe Commerce [!DNL Site-Wide Analysis Tool]-Bericht

>[!IMPORTANT]
>
>Ab dem 23. April 2024 wird die [!DNL Site-Wide Analysis Tool] für alle Adobe Commerce On-Premise-Kunden eingestellt.

Dieser Artikel enthält eine Beschreibung des [!DNL Site-Wide Analysis Tool], der automatisch monatlich oder vierteljährlich für Kunden von Adobe Commerce auf Cloud-Infrastruktur generiert wird.

>[!NOTE]
>
>In Adobe Commerce in Cloud-Infrastrukturen der Version 2.4.1 und höher ist [!DNL Site-Wide Analysis Tool] über das Commerce Admin Panel verfügbar. Daher können [!DNL Site-Wide Analysis Tool] Berichte direkt vom Kunden ausgeführt werden. Weitere Informationen zum Zugriff finden Sie im [[!DNL Site-Wide Analysis Tool] Handbuch](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/access.html?lang=de).

## Was ist [!DNL Site-Wide Analysis Tool]?

[!DNL Site-Wide Analysis Tool] ist eine SaaS-Anwendung, die eine End-to-End-„Point-in-Time“-Analyse der Kunden-Site durchführt (innerhalb der [!DNL Site-Wide Analysis Tool]-Umgebung, nicht auf der Site des Kunden). Alle [!DNL Site-Wide Analysis Tool] Kundeninformationen werden nach vorher festgelegten Zeitplänen von alle 3 Stunden bis einmal täglich erfasst. Das bedeutet, dass [!DNL Site-Wide Analysis Tool] die Daten der Kunden-Sites ständig auf Ergebnisse hin analysiert.

## Was ist ein [!DNL Site-Wide Analysis Tool]?

Der [!DNL Site-Wide Analysis Tool]-Bericht ist eine Liste von Ergebnissen (Problemen) mit Self-Service-Empfehlungen (Best Practices), die in einem PDF-Formular über das Support-Ticket-System von Adobe Commerce an Kunden gesendet werden können.

## Welche Informationen sind in einem [!DNL Site-Wide Analysis Tool] enthalten?

Die im [!DNL Site-Wide Analysis Tool] bereitgestellten Site-Informationen umfassen Folgendes:

* Fund
   * Übersicht, einschließlich einer „Priorität“ für die Reihenfolge der Implementierungskorrektur
   * Suchbeschreibung
   * Voraussetzungen, falls vorhanden
   * Site Impact(s)
   * Ursache(n)
   * Empfehlung(en)
* Ausnahmeprotokolle
   * Informationen zu Protokollausnahmen
   * Datum des letzten Auftretens
   * Häufigkeit, in der die Ausnahme auftritt

## Wer erhält die automatisierten monatlichen [!DNL Site-Wide Analysis Tool]?

Derzeit erhalten Kundinnen und Kunden mit einem niedrigen [!DNL Site-Wide Analysis Tool]-Konsistenzindex (mindestens bei dem derzeit festgelegten Leistungsschwellenwert) über das Support-Ticket-System einen monatlichen [!DNL Site-Wide Analysis Tool] für ihre Produktionsumgebung.

## Wer erhält die automatisierten vierteljährlichen [!DNL Site-Wide Analysis Tool]?

Alle Kundinnen und Kunden erhalten unabhängig vom [!DNL Site-Wide Analysis Tool] Gesundheitsindex über das Support-Ticket-System einen vierteljährlichen [!DNL Site-Wide Analysis Tool] für ihre Produktionsumgebung.

## Wie werden Berichte bereitgestellt?

[!DNL Site-Wide Analysis Tool] Berichte werden automatisch monatlich oder vierteljährlich über das Adobe Commerce Support-Ticket-System bereitgestellt. [!DNL Site-Wide Analysis Tool] Berichte können auch manuell über das [!DNL Site-Wide Analysis Tool]-Dashboard generiert und auf Ihrem Desktop gespeichert werden. Diese [!DNL Site-Wide Analysis Tool] können dann als Anhänge per E-Mail gesendet werden.

>[!NOTE]
>
>Nach Anwendung einer Empfehlung werden bei der manuellen Erstellung eines Berichts die Empfehlungen nicht aktualisiert - es kann einige Tage dauern, bis er aus der [!DNL Site-Wide Analysis Tool Dashboard] entfernt wird.
