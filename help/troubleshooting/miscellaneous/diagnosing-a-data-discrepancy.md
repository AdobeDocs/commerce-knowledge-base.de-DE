---
title: Diagnose einer Datendiskrepanz
description: Dieser Artikel enthält Lösungen zur Behebung von Diskrepanzen zwischen einem Magento Business Intelligence-Bericht (MBI) und einem Abfrage- oder Drittanbieterbericht.
exl-id: 7d1156cb-9e9b-4426-a0ca-8890b815c245
feature: Commerce Intelligence
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# Diagnose einer Datendiskrepanz

Dieser Artikel enthält Lösungen zur Behebung von Diskrepanzen zwischen einem Magento Business Intelligence-Bericht (MBI) und einem Abfrage- oder Drittanbieterbericht.

Je nach Komplexität Ihrer Analyse kann die Erstellung des entsprechenden MBI-Berichts Vertrautheit mit einer Reihe verschiedener Facetten der Plattform erfordern. Diese Checkliste und die zugehörigen Links helfen Ihnen, die Logik hinter Ihrem Bericht zu verstehen, sodass Sie die Quelle aller Diskrepanzen identifizieren können.

1. Wenn ein anderes Teammitglied den Bericht erstellt hat, bestätigen Sie zunächst die Zielsetzung und die Parameter seiner Analyse.
1. Generieren Sie erwartete Datenpunkte, die mit dem MBI-Bericht verglichen werden sollen, basierend auf einer Abfrage, einem Reporting-Tool von Drittanbietern oder einer Formel.
1. Überprüfen und bestätigen Sie die [Metrik](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-metrics.html?lang=de)Definition(en), entweder über den Metrik-Link im Report Builder oder indem Sie die Registerkarte [Systemzusammenfassung](https://support.magento.com/hc/en-us/articles/360016730971-Understand-View-definitions-of-metrics-filters-columns-and-column-references-in-the-System-Summary) aufrufen:
   * Datentabelle
   * Bedienung
   * Operandenspalte, einschließlich der Berechnung, falls sie abgeleitet ist (über Systemzusammenfassung)
   * Zeitstempel
   * Für Abonnementmetriken: Start- und Enddatum
   * Es werden Filter angewendet, einschließlich [&#x200B; in &#x200B;](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-filters.html?lang=de) Filtersätzen enthaltenen
1. Überprüfen und bestätigen Sie andere Datenmanipulationen im Bericht:
   * Berechnete Formeln
   * [Gruppierungen](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html?lang=de#groupby)
   * [Perspektiven](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html?lang=de)
   * [Zeitoptionen](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html?lang=de)
   * Für [Kohortenanalyse](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis): Kohortendatum
   * Für [Kohortenanalyse](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis): Kohortenperspektive
1. Wenn die Diskrepanz aktuelle Daten betrifft, bestätigen Sie den neuesten verfügbaren Datenpunkt, indem Sie den Abschnitt **Details aktualisieren** auf der Seite Verbindungen konsultieren.
1. Wenn eine in der Analyse verwendete Metrik auf einer Tabelle aus Ihrer Datenbank basiert, in der Zeilen jemals aus dieser Tabelle gelöscht werden, bestätigen Sie dem MBI-Supportteam, dass die Tabelle auf gelöschte Zeilen überprüft wird, sowie die Häufigkeit der erneuten Überprüfung und die [Replikationsmethode](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/opt-db-analysis.html?lang=de) für die Tabelle.
1. Wenn in der Analyse verwendete Spalten geändert werden können, nachdem eine Zeile hinzugefügt wurde, bestätigen Sie mit -Support, dass diese Spalten [auf Änderungen überprüft](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/warehouse-manager/cfg-data-rechecks.html?lang=de) sowie die Häufigkeit der erneuten Überprüfung.

**Immer noch verblüfft?** Keine Sorge - wir sind hier, um zu helfen. Senden Sie uns eine Anfrage mit [diesen Anweisungen](/help/troubleshooting/miscellaneous/mbi-data-discrepancies.md).

## Verwandtes Lesen

[Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/de/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook
