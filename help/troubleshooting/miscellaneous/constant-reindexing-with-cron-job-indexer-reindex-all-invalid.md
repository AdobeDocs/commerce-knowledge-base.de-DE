---
title: Indizes ungültig gemacht und „INDEXER_REINDEX_ALL_INVALID“ werden ständig ausgeführt
description: Indizes ungültig gemacht und „INDEXER_REINDEX_ALL_INVALID“ werden ständig ausgeführt
labels: troubleshooting,error,indexing,crons,site performance,adobe commerce,magento,cron,indexer_reindex_all_invalid,SQL,MySQL,reindex
exl-id: c7148ef4-2155-4d4c-869b-1d08de4af598
feature: B2B, Catalog Management, Categories, Observability, Price Indexer
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# Indizes werden ungültig gemacht und `indexer_reindex_all_invalid` ständig ausgeführt

Dieser Artikel bietet eine mögliche Problemumgehung, wenn Ihre Site Leistungsprobleme aufweist, die durch eine ständige Neuindizierung verursacht werden. Dies ist darauf zurückzuführen, dass der [!DNL cron] Auftrag `indexer_reindex_all_invalid` kontinuierlich ausgeführt und die Caches bei [!DNL reindex] bereinigt werden.

## Betroffene Produkte und Versionen

* Adobe Commerce (Cloud und On-Premises) 2.4.0+ (Da **[!UICONTROL Category Permissions]** nur eine Adobe-Commerce-Funktion ist, hat dies keine Auswirkungen auf die Magento Open Source.)

## Problem

In [!DNL New Relic One] sollten Fehlerprotokolle `indexer_update_all_views` zeigen, die häufig mit einer Zeit von > 1 Sekunde ausgeführt werden (d. h., es wird etwas verarbeitet).

## Ursache

Wenn der Adobe Commerce-Core-Importer ausgeführt wird (manuell oder durch [!DNL cron]), wird ein Satz von Plug-ins für mehrere Kernmodule ausgeführt, um zu bestimmen, welche Indizes ungültig gemacht werden sollen.

Das Problem tritt auf, wenn das **[!UICONTROL Category Permissions]** im [!DNL Commerce Admin] aktiviert ist. Wenn dies „true“ ist, werden die Produkt- und Kategorieindizes (und verknüpften Indizes) immer durch das Plug-in des Moduls ungültig, wenn ein Import ausgeführt wird. Wenn die standardmäßigen Importtypen untersucht werden, wirken sie sich alle auf **[!UICONTROL Category Permissions]** aus. Invalidierung wird erwartet.

Wenn auf einer Site B2B-Module aktiviert sind, wird **[!UICONTROL Shared Catalog]** außerdem aktiviert und **[!UICONTROL Category Permissions]** gesperrt. Wenn Sie **[!UICONTROL Shared Catalog]** ausschalten, wird **[!UICONTROL Category Permissions]** entsperrt, aber nicht ausgeschaltet.

<u>Überprüfen [!DNL cron] Protokolle in Ihrer [!DNL MySQL]-Datenbank</u>:

Wenn Sie sich bei Ihrer [!DNL MySQL]-Datenbank anmelden, können diese Ihr `cron` auf den **[!DNL reindex all indexes]** überprüfen.
Das **sollte** oft vorkommen, aber der wichtige Faktor ist, dass der Prozess eine von zwei möglichen Dingen tut.

Der Prozess kann nur eine der beiden folgenden Aktionen durchführen:

1. Nichts: Es würde 0 bis 1 Sekunde (eine Sekunde oder weniger) dauern - der Prozess prüft, ob er etwas tun muss, und stoppt dann, wenn er nichts tun muss.
1. Alles [!DNL Reindex]: Es wird immer Zeit brauchen - in der Regel Minuten.

Normalerweise würden Sie viele Vorkommnisse des Prozesses sehen wollen, aber mit einer Ausführungszeit von weniger als 1 Sekunde.
Ein Händler kann daher diese [!DNL MySQL]-Abfrage verwenden, um Transaktionen zu finden, deren Ausführung **mehr als 1**) dauert:

```sql
SELECT TIMESTAMPDIFF(SECOND, executed_at, finished_at) AS period FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' HAVING period > 1
```

Sie können sehen, wie lange ein Zeitraum aufgezeichnet wird, indem Sie Folgendes ausführen:

```sql
SELECT executed_at FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' AND executed_at IS NOT NULL ORDER BY executed_at ASC LIMIT 1;
```

Wenn Ihnen dies nicht genügend Zeit für eine korrekte Bewertung gibt, können Sie die Zeit erhöhen, die ein erfolgreicher `cron` im Protokoll gespeichert wird, indem Sie dieser Anleitung [[!DNL Cron] (Geplante Aufgaben)](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html?lang=de) folgen, und den **[!DNL Success History Lifetime]** erhöhen (der Standardwert ist nur 60 Minuten).


## Lösung

Erweitern Sie `Magento\CatalogPermissions\Model\Indexer\Plugin\Import` so, dass die `afterImportSource` den benutzerdefinierten Importer ausschließt.

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

Dabei ist `ENTITY_CODE` der Wert, der für den Parameter „Entity Name“ in der `import.xml` für das benutzerdefinierte Import-Tool verwendet wird.

## Verwandtes Lesen

[configure [!DNL cron] jobs](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html?lang=de) im Adobe Commerce Operations Configuration Guide.
