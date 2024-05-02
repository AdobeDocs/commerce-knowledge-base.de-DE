---
title: Invalidierte Indizes und "indexer_reindex_all_invalid" werden ständig ausgeführt
description: Invalidierte Indizes und "indexer_reindex_all_invalid" werden ständig ausgeführt
labels: troubleshooting,error,indexing,crons,site performance,adobe commerce,magento,cron,indexer_reindex_all_invalid,SQL,MySQL,reindex
exl-id: c7148ef4-2155-4d4c-869b-1d08de4af598
feature: B2B, Catalog Management, Categories, Observability, Price Indexer
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# Indizes wurden ungültig gemacht und `indexer_reindex_all_invalid` laufend

Dieser Artikel bietet eine mögliche Problemumgehung, wenn auf Ihrer Site Leistungsprobleme auftreten, die durch eine ständige Neuindizierung verursacht werden. Dies wird durch die [!DNL cron] job `indexer_reindex_all_invalid` fortlaufend laufen und gereinigte Caches [!DNL reindex].

## Betroffene Produkte und Versionen

* Adobe Commerce (Cloud &amp; On-Premise) 2.4.0+ (As **[!UICONTROL Category Permissions]** ist eine Funktion, die nur für Adobe-Commerce verfügbar ist. Sie hat keine Auswirkungen auf die Magento Open Source.)

## Problem

In [!DNL New Relic One] Fehlerprotokolle zeigen `indexer_update_all_views` mehrmals mit einer Zeit > 1 Sekunde ausgeführt werden (d. h. es wird etwas verarbeitet).

## Ursache

Wenn das Adobe Commerce-Core-Importtool ausgeführt wird (manuell oder von [!DNL cron]), dann wird eine Reihe von Plug-ins über mehrere Kernmodule hinweg ausgeführt, um zu bestimmen, welche Indizes ungültig gemacht werden sollen.

Das Problem tritt auf, wenn die **[!UICONTROL Category Permissions]** -Modul aktiviert ist, wird im [!DNL Commerce Admin]. Wenn dies zutrifft, werden die Produkt- und Kategorienindizes (und verknüpften Indizes) durch das Plug-in des Moduls immer invalidiert, wenn ein Import ausgeführt wird. Werden die pauschalen Einfuhrtypen untersucht, so wirken sich sie alle auf **[!UICONTROL Category Permissions]**. Die Invalidierung ist zu erwarten.

Wenn für eine Site B2B-Module aktiviert sind, muss darüber hinaus **[!UICONTROL Shared Catalog]** aktiviert ist, wird aktiviert und gesperrt **[!UICONTROL Category Permissions]**. Ausschalten **[!UICONTROL Shared Catalog]** wird entsperrt **[!UICONTROL Category Permissions]**, aber nicht ausschalten.

<u>Überprüfung [!DNL cron] Login in [!DNL MySQL] Datenbank</u>:

Wenn Sie sich bei Ihrem [!DNL MySQL] -Datenbank, können sie Ihre `cron` log für **[!DNL reindex all indexes]** -Prozess.
Diese **sollte** erscheint oft, aber der wichtige Faktor ist, dass der Prozess eine von zwei möglichen Dingen ausführt.

Der Prozess kann nur eine der beiden folgenden Aktionen durchführen:

1. Nichts: Es würde 0 bis 1 Sekunde (eine Sekunde oder weniger) dauern - der Prozess prüft, ob er etwas tun muss, und stoppt dann, wenn er nichts tun muss.
1. [!DNL Reindex] alles: Es dauert immer Zeit - normalerweise Minuten.

Normalerweise möchten Sie viele Vorkommen des Prozesses sehen, jedoch mit einer Ausführungszeit von weniger als 1 Sekunde.
Ein Händler kann dies daher verwenden [!DNL MySQL] Abfrage zum Finden von Transaktionen, die **mehr als 1 Sekunde** zum Ausführen:

```sql
SELECT TIMESTAMPDIFF(SECOND, executed_at, finished_at) AS period FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' HAVING period > 1
```

Sie können sehen, wie lange ein Zeitraum aufgezeichnet wurde, indem Sie Folgendes ausführen:

```sql
SELECT executed_at FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' AND executed_at IS NOT NULL ORDER BY executed_at ASC LIMIT 1;
```

Wenn Ihnen dies nicht genügend Zeit gibt, um eine korrekte Bewertung vorzunehmen, können Sie die Zeit für einen erfolgreichen Test verlängern `cron` Der Prozess wird im folgenden Protokoll beibehalten: [[!DNL Cron] (geplante Aufgaben)](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) und erhöhen Sie **[!DNL Success History Lifetime]** -Wert (der Standardwert ist nur 60 Minuten).


## Lösung

Erweitern `Magento\CatalogPermissions\Model\Indexer\Plugin\Import` damit die `afterImportSource` -Methode schließt das benutzerdefinierte Importtool aus.

```
    public function afterImportSource(\Magento\ImportExport\Model\Import $subject, $import)
    {
        if ($this->config->isEnabled() && $subject->getEntity() !== 'ENTITY_CODE') {
            $this->indexerRegistry->get(\Magento\CatalogPermissions\Model\Indexer\Category::INDEXER_ID)->invalidate();
            $this->indexerRegistry->get(\Magento\CatalogPermissions\Model\Indexer\Product::INDEXER_ID)->invalidate();
        }
        return $import;
    }
```

Wo `ENTITY_CODE` ist der für den Entitätsnamenparameter im `import.xml` -Datei für das benutzerdefinierte Importtool.

## Verwandtes Lesen

[Konfigurieren [!DNL cron] Aufträge](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) im Konfigurationshandbuch für den Betrieb von Adobe Commerce.
