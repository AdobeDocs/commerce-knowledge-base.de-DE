---
title: Datendiskrepanz diagnostizieren
description: Dieser Artikel bietet Lösungen für die Behebung von Diskrepanzen zwischen einem Magento Business Intelligence-Bericht (MBI) und einer Abfrage oder einem Drittanbieter-Bericht.
exl-id: 7d1156cb-9e9b-4426-a0ca-8890b815c245
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Datendiskrepanz diagnostizieren

Dieser Artikel bietet Lösungen für die Behebung von Diskrepanzen zwischen einem Magento Business Intelligence-Bericht (MBI) und einer Abfrage oder einem Drittanbieter-Bericht.

Je nach Komplexität Ihrer Analyse kann die Erstellung des entsprechenden MBI-Berichts die Kenntnis verschiedener Facetten der Plattform erfordern. Diese Checkliste und die zugehörigen Links helfen Ihnen dabei, die Logik Ihres Berichts zu verstehen, sodass Sie die Ursache etwaiger Diskrepanzen identifizieren können.

1. Wenn ein anderes Mitglied Ihres Teams den Bericht erstellt hat, bestätigen Sie zunächst das Ziel und die Parameter seiner Analyse.
1. Generieren Sie erwartete Datenpunkte, die basierend auf einer Abfrage, einem Reporting-Tool eines Drittanbieters oder einer Formel mit dem MBI-Bericht verglichen werden.
1. Überprüfen und bestätigen Sie die Definition(en) für [metric](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-metrics.html), entweder über den Metriklink im Report Builder oder über die Registerkarte [Systemzusammenfassung](https://support.magento.com/hc/en-us/articles/360016730971-Understand-View-definitions-of-metrics-filters-columns-and-column-references-in-the-System-Summary):
   * Datentabelle
   * Vorgang
   * Operanden-Spalte, einschließlich der Berechnung, falls sie abgeleitet wurde (über Systemübersicht)
   * Zeitstempel
   * Für Abonnementmetriken: Start- und Enddatum
   * Filter, einschließlich der in angewendeten [Filtersätzen](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-filters.html) enthaltenen Filter
1. Überprüfen und bestätigen Sie andere Datenmanipulationen im Bericht:
   * Formeln berechnet
   * [Groupings](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html#groupby)
   * [Perspektiven](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html)
   * [Zeitoptionen](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html)
   * Für [Kohortenanalyse](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis): Kohortendatum
   * Für [Kohortenanalyse](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis): Kohortenperspektive
1. Wenn es sich bei der Diskrepanz um aktuelle Daten handelt, bestätigen Sie den neuesten verfügbaren Datenpunkt, indem Sie den Abschnitt **Details aktualisieren** auf der Seite Verbindungen durchsuchen.
1. Wenn eine in der Analyse verwendete Metrik auf einer Tabelle aus Ihrer Datenbank basiert, in der Zeilen jemals aus dieser Tabelle gelöscht werden, bestätigen Sie mit dem MBI-Supportteam, dass die Tabelle auf gelöschte Zeilen überprüft wird, sowie die Häufigkeit der Überprüfung und die [Replikationsmethode](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/opt-db-analysis.html) für die Tabelle.
1. Wenn in der Analyse verwendete Spalten nach dem Hinzufügen einer Zeile geändert werden können, überprüfen Sie mit der Unterstützung, dass diese Spalten auf Änderungen überprüft werden [](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/warehouse-manager/cfg-data-rechecks.html) sowie die Häufigkeit der erneuten Überprüfung.

**Noch nicht angehalten?** Keine Sorge - wir sind hier, um zu helfen. Senden Sie uns eine Anfrage mit [diesen Anweisungen](/help/troubleshooting/miscellaneous/mbi-data-discrepancies.md).
