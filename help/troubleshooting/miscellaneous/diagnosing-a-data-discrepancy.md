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
1. Überprüfen und bestätigen Sie die [Metrik](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-metrics.html) Definition(en), entweder über den Metrik-Link in Report Builder oder durch Besuch der [Systemzusammenfassung](https://support.magento.com/hc/en-us/articles/360016730971-Understand-View-definitions-of-metrics-filters-columns-and-column-references-in-the-System-Summary) tab:
   * Datentabelle
   * Vorgang
   * Operanden-Spalte, einschließlich der Berechnung, falls sie abgeleitet wurde (über Systemübersicht)
   * Zeitstempel
   * Für Abonnementmetriken: Start- und Enddatum
   * Filter, einschließlich der in allen [Filtersätze](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-filters.html) angewendet
1. Überprüfen und bestätigen Sie andere Datenmanipulationen im Bericht:
   * Formeln berechnet
   * [Gruppierungen](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html#groupby)
   * [Perspektiven](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html)
   * [Zeitoptionen](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html)
   * Für [Kohortenanalyse](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis): Datum der Kohorte
   * Für [Kohortenanalyse](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis): Kohortenperspektive
1. Wenn es bei der Diskrepanz um aktuelle Daten geht, bestätigen Sie den neuesten verfügbaren Datenpunkt, indem Sie die **Details aktualisieren** auf der Seite Verbindungen .
1. Wenn eine in der Analyse verwendete Metrik auf einer Tabelle aus Ihrer Datenbank basiert, in der Zeilen jemals aus dieser Tabelle gelöscht werden, bestätigen Sie mit dem MBI-Supportteam, dass die Tabelle auf gelöschte Zeilen überprüft wird, sowie die Häufigkeit der Überprüfung und der [Replikationsmethode](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/opt-db-analysis.html) für die Tabelle.
1. Wenn in der Analyse verwendete Spalten nach dem Hinzufügen einer Zeile geändert werden können, bestätigen Sie mit der Unterstützung, dass diese Spalten [überprüft auf Änderungen](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/warehouse-manager/cfg-data-rechecks.html)sowie die Häufigkeit der Überprüfung.

**Ist noch nicht da?** Keine Sorge - wir sind hier, um zu helfen. Senden Sie uns eine Anfrage mit [diese Anweisungen](/help/troubleshooting/miscellaneous/mbi-data-discrepancies.md).
