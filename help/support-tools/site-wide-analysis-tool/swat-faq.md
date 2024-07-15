---
title: Adobe Commerce [!DNL Site-Wide Analysis Tool] Häufig gestellte Fragen zu Berichten
description: Erfahren Sie mehr über den [!DNL Site-Wide Analysis Tool], ein proaktives Self-Service-Tool und ein zentrales Repository, das detaillierte Systemeinblicke und Empfehlungen enthält, um die Sicherheit und Bedienbarkeit Ihrer Adobe Commerce-Installation sicherzustellen.
exl-id: 7c843d55-9e2c-4b18-8859-0ebad0ae28cf
feature: Best Practices, Saas, Support, Tools and External Services
role: Admin
source-git-commit: 580ad148cd4346868cd9892a1ae9a4d85f73edce
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Häufig gestellte Fragen zu Adobe Commerce [!DNL Site-Wide Analysis Tool] Berichten

>[!IMPORTANT]
>
>Mit Wirkung vom 23. April 2024 wird der [!DNL Site-Wide Analysis Tool] für alle Adobe Commerce-Kunden vor Ort eingestellt.

In diesem Artikel wird der Bericht [!DNL Site-Wide Analysis Tool] beschrieben, der monatlich oder vierteljährlich automatisch für Adobe Commerce-Kunden mit Cloud-Infrastruktur erstellt wird.

>[!NOTE]
>
>In Adobe Commerce ab der Cloud-Infrastruktur-Version 2.4.1 ist [!DNL Site-Wide Analysis Tool] über das Commerce Admin Panel verfügbar. Daher können [!DNL Site-Wide Analysis Tool] Berichte direkt vom Kunden ausgeführt werden. Weitere Informationen zum Zugriff finden Sie im [[!DNL Site-Wide Analysis Tool] Handbuch](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/access.html).

## Was ist [!DNL Site-Wide Analysis Tool]?

[!DNL Site-Wide Analysis Tool] ist eine SaaS-Anwendung, die eine End-to-End-Site-Analyse der Point-in-Time-Kundenseite durchführt (innerhalb der [!DNL Site-Wide Analysis Tool]-Umgebung, nicht auf der Site des Kunden). Alle [!DNL Site-Wide Analysis Tool]-bezogenen Kunden-Site-Informationen werden in vordefinierten Zeitplänen von alle 3 Stunden bis einmal täglich erfasst. Das bedeutet, dass [!DNL Site-Wide Analysis Tool] die Site-Daten der Kunden laufend auf Ergebnisse analysiert.

## Was ist ein [!DNL Site-Wide Analysis Tool] Bericht?

Der [!DNL Site-Wide Analysis Tool]-Bericht ist eine Liste von Ergebnissen (Problemen) mit Empfehlungen zu Self-Service und Best Practices, die über das Support-Ticketsystem von Adobe Commerce an PDF-Kunden gesendet werden können.

## Welche Informationen sind in einem [!DNL Site-Wide Analysis Tool] -Bericht enthalten?

Die im Bericht [!DNL Site-Wide Analysis Tool] bereitgestellten Site-Informationen umfassen:

* Suchen
   * Übersicht, einschließlich einer &quot;Priorität&quot;für die Reihenfolge der Implementierungskorrektur
   * Suchbeschreibung
   * Gegebenenfalls Voraussetzungen
   * Site-Auswirkungen
   * Root Ursache(n)
   * Empfehlung(en)
* Ausnahmeprotokolle
   * Informationen zu Protokollausnahmen
   * Datum des letzten Auftretens
   * Häufigkeit, mit der die Ausnahme auftritt

## Wer erhält die automatisierten monatlichen [!DNL Site-Wide Analysis Tool] Berichte?

Derzeit erhalten Kunden mit einem niedrigen [!DNL Site-Wide Analysis Tool] Konsistenzindex (am oder unter dem derzeit festgelegten Leistungsschwellenwert) über das Support-Ticketsystem einen monatlichen [!DNL Site-Wide Analysis Tool] Bericht für ihre Produktionsumgebung.

## Wer erhält die automatisierten vierteljährlichen [!DNL Site-Wide Analysis Tool] Berichte?

Alle Kunden erhalten über das Support-Ticketsystem einen vierteljährlichen [!DNL Site-Wide Analysis Tool] Bericht für ihre Produktionsumgebung, unabhängig vom [!DNL Site-Wide Analysis Tool] Health Index.

## Wie werden Berichte bereitgestellt?

[!DNL Site-Wide Analysis Tool] -Berichte werden automatisch monatlich oder vierteljährlich über das Adobe Commerce-Support-Ticketsystem bereitgestellt. [!DNL Site-Wide Analysis Tool] -Berichte können auch manuell über das Dashboard [!DNL Site-Wide Analysis Tool] generiert und auf Ihrem Desktop gespeichert werden. Diese [!DNL Site-Wide Analysis Tool] -Berichte können dann als Anhänge per E-Mail versendet werden.

>[!NOTE]
>
>Nach Anwendung einer Empfehlung werden die Empfehlungen durch manuelles Generieren eines Berichts nicht aktualisiert. Es kann einige Tage dauern, bis er aus dem [!DNL Site-Wide Analysis Tool Dashboard] entfernt wird.
