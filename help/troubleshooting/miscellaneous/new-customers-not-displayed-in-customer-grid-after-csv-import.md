---
title: Neue Kunden werden nach dem CSV-Import nicht im Kundenraster angezeigt
description: Dieser Artikel enthält eine Fehlerbehebung für das Problem, wenn Sie unter "Kunden** &gt; **Alle Kunden** nach einem Import aus einer .csv-Datei keine neuen Kunden sehen können. Die Lösung besteht darin, den Indexer "customer_grid"auf den Modus "Update on Save"festzulegen und das Kundenraster manuell neu zu indizieren.
exl-id: e4d9d60a-a0d1-4602-924e-a338e56de61d
feature: Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Neue Kunden werden nach dem CSV-Import nicht im Kundenraster angezeigt

In diesem Artikel wird das Problem behoben, das auftritt, wenn neue Kunden nicht unter **Kunden** > **Alle Kunden** nach einem Import aus einer `.csv` -Datei angezeigt werden. Die Lösung besteht darin, den `customer_grid`-Indexer auf den Modus &quot;Beim Speichern aktualisieren&quot;zu setzen und das Kundenraster manuell neu zu indizieren.

## Betroffene Versionen

* Adobe Commerce On-Premise 2.2.0 und höher
* Adobe Commerce auf Cloud-Infrastruktur 2.2.0 und höher

## Problem

Nach dem Import neuer Kunden aus einer `.csv` -Datei mithilfe der nativen Adobe Commerce-Importfunktion können Sie die neuen Kundendatensätze unter **Kunden** > **Alle Kunden** im Admin möglicherweise erst dann anzeigen, wenn Sie den `customer_grid` -Indexer manuell neu indizieren.

## Ursache

Der Indexierungsmodus &quot;Auf Zeitplan aktualisieren&quot;in Adobe Commerce 2.2.0 und höher unterstützt den `customer_grid` -Indexer aufgrund von Leistungsproblemen nicht.

## Lösung

Konfigurieren Sie den `customer_grid`-Indexer, der im Modus &quot;Beim Speichern aktualisieren&quot;neu indiziert werden soll. Gehen Sie dazu wie folgt vor:

1. Melden Sie sich bei Commerce Admin an.
1. Klicken Sie auf **System** > **Tools** > **Indexverwaltung**.
1. Aktivieren Sie das Kontrollkästchen neben Customer Grid Indexer.
1. Wählen Sie in der Dropdownliste **Aktionen** die Option *Beim Speichern aktualisieren* aus.
1. Klicken Sie auf **Senden**.

Es wird außerdem empfohlen, den `customer_grid` -Indexer manuell neu zu indizieren, nachdem der Indizierungsmodus konfiguriert wurde, um sicherzustellen, dass der Index aktuell ist und mit Cron funktioniert. Verwenden Sie den folgenden Befehl, um eine manuelle Neuindizierung durchzuführen:

`bin/magento indexer:reindex customer_grid`

## Weitere Informationen

Links zu verwandten Themen in unserer Entwicklerdokumentation:

* [Indizierungsübersicht](https://developer.adobe.com/commerce/php/development/components/indexing/)
* [Indexer verwalten](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers)
