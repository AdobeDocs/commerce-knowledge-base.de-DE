---
title: Neue Kunden werden nach dem CSV-Import nicht im Kundenraster angezeigt
description: Dieser Artikel bietet eine Lösung für das Problem, wenn nach einem Import aus einer CSV-Datei unter **Customers** &gt; **All Customers** keine neuen Kunden angezeigt werden. Die Lösung besteht darin, den Indexer „customer_grid“ auf den Modus „Beim Speichern aktualisieren“ einzustellen und das Kundenraster manuell neu zu indizieren.
exl-id: e4d9d60a-a0d1-4602-924e-a338e56de61d
feature: Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Neue Kunden werden nach dem CSV-Import nicht im Kundenraster angezeigt

Dieser Artikel bietet eine Lösung für das Problem, wenn Sie nach einem Import aus einer `.csv`-Datei keine neuen Kunden unter **Kunden** > **Alle**&quot; sehen. Die Lösung besteht darin, den `customer_grid` Indexer auf den Modus „Beim Speichern aktualisieren“ einzustellen und das Kundenraster manuell neu zu indizieren.

## Betroffene Versionen

* Adobe Commerce On-Premises 2.2.0 und höher
* Adobe Commerce auf Cloud-Infrastruktur 2.2.0 und höher

## Problem

Nach dem Import neuer Kunden aus einer `.csv` mit der nativen Adobe Commerce-Importfunktion können Sie die neuen Kundendatensätze möglicherweise erst dann unter **Kunden** > **Alle Kunden** im Admin sehen, wenn Sie den `customer_grid`-Indexer manuell neu indizieren.

## Ursache

Der Indizierungsmodus „Update on Schedule“ in Adobe Commerce 2.2.0 und höher unterstützt den `customer_grid` aufgrund von Leistungsproblemen nicht.

## Lösung

Konfigurieren Sie den neu zu indizierenden `customer_grid`-Indexer mithilfe des Modus „Beim Speichern aktualisieren“. Gehen Sie dazu wie folgt vor:

1. Melden Sie sich beim Commerce Admin an.
1. Klicken Sie auf **System** > **Tools** > **Indexverwaltung**.
1. Aktivieren Sie das Kontrollkästchen neben dem Kundenraster-Indexer.
1. Wählen Sie in **Dropdown** Liste „Aktionen“ die Option *Aktualisieren beim Speichern* aus.
1. Klicken Sie **Senden**.

Es wird außerdem empfohlen, den `customer_grid` Indexer nach der Konfiguration des Indexmodus manuell neu zu indizieren, um sicherzustellen, dass der Index auf dem neuesten Stand ist und mit Cron arbeiten kann. Verwenden Sie den folgenden Befehl, um eine manuelle Neuindizierung durchzuführen:

`bin/magento indexer:reindex customer_grid`

## Weitere Informationen

Links zu verwandten Themen in unserer Entwicklerdokumentation:

* [Indizierungsübersicht](https://developer.adobe.com/commerce/php/development/components/indexing/)
* [Indexer verwalten](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/cli/manage-indexers)
