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

# Indizes ungültig gemacht und `indexer_reindex_all_invalid` laufend ausgeführt

Dieser Artikel bietet eine mögliche Problemumgehung, wenn auf Ihrer Site Leistungsprobleme auftreten, die durch eine ständige Neuindizierung verursacht werden. Dies wird durch den fortlaufenden [!DNL cron] Auftrag `indexer_reindex_all_invalid` verursacht, der auf [!DNL reindex] gesäubert wird.

## Betroffene Produkte und Versionen

* Adobe Commerce (Cloud &amp; On-Premise) 2.4.0+ (Da **[!UICONTROL Category Permissions]** nur eine Adobe-Commerce-Funktion ist, hat dies keine Auswirkungen auf die Magento Open Source.)

## Problem

In den [!DNL New Relic One] -Fehlerprotokollen sollte `indexer_update_all_views` angezeigt werden, die mehrmals mit einer Zeit > 1 Sekunde ausgeführt werden (d. h. es wird etwas verarbeitet).

## Ursache

Wenn das Adobe Commerce-Core-Importtool ausgeführt wird (manuell oder durch [!DNL cron]), wird eine Reihe von Plug-ins über mehrere Hauptmodule hinweg ausgeführt, um zu bestimmen, welche Indizes ungültig gemacht werden sollen.

Das Problem tritt auf, wenn das **[!UICONTROL Category Permissions]**-Modul in der [!DNL Commerce Admin] aktiviert ist. Wenn dies zutrifft, werden die Produkt- und Kategorienindizes (und verknüpften Indizes) durch das Plug-in des Moduls immer invalidiert, wenn ein Import ausgeführt wird. Wenn die standardmäßigen Einfuhrtypen untersucht werden, wirken sich diese auf **[!UICONTROL Category Permissions]** aus. Die Invalidierung ist zu erwarten.

Wenn für eine Site B2B-Module aktiviert sind, wird bei Aktivierung von **[!UICONTROL Shared Catalog]** außerdem **[!UICONTROL Category Permissions]** aktiviert und gesperrt. Wenn Sie **[!UICONTROL Shared Catalog]** ausschalten, wird **[!UICONTROL Category Permissions]** entsperrt, aber nicht ausgeschaltet.

<u>Überprüfen der [!DNL cron] Protokolle in Ihrer [!DNL MySQL] Datenbank</u>:

Wenn Sie sich in Ihrer [!DNL MySQL] -Datenbank anmelden, können sie Ihr `cron`-Protokoll auf den **[!DNL reindex all indexes]**-Prozess überprüfen.
Dieser **sollte** mehrmals erscheinen, aber der wichtige Faktor ist, dass der Prozess eines von zwei möglichen Dingen ausführt.

Der Prozess kann nur eine der beiden folgenden Aktionen durchführen:

1. Nichts: Es würde 0 bis 1 Sekunde (eine Sekunde oder weniger) dauern - der Prozess prüft, ob er etwas tun muss, und stoppt dann, wenn er nichts tun muss.
1. [!DNL Reindex] alles: Es dauert immer Zeit - normalerweise Minuten.

Normalerweise möchten Sie viele Vorkommen des Prozesses sehen, jedoch mit einer Ausführungszeit von weniger als 1 Sekunde.
Ein Händler kann diese [!DNL MySQL] -Abfrage daher verwenden, um Transaktionen zu finden, für die die Ausführung von **mehr als 1 Sekunde** dauert:

```sql
SELECT TIMESTAMPDIFF(SECOND, executed_at, finished_at) AS period FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' HAVING period > 1
```

Sie können sehen, wie lange ein Zeitraum aufgezeichnet wurde, indem Sie Folgendes ausführen:

```sql
SELECT executed_at FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' AND executed_at IS NOT NULL ORDER BY executed_at ASC LIMIT 1;
```

Wenn Ihnen dies keinen ausreichend langen Zeitraum für eine ordnungsgemäße Bewertung gibt, können Sie die Zeit, in der ein erfolgreicher `cron` -Prozess im Protokoll aufbewahrt wird, nach diesem [[!DNL Cron] (geplanten Aufgaben)](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) -Handbuch und dem Erhöhen des **[!DNL Success History Lifetime]** -Werts erhöhen (der Standardwert beträgt nur 60 Minuten).


## Lösung

Erweitern Sie `Magento\CatalogPermissions\Model\Indexer\Plugin\Import` , sodass die Methode `afterImportSource` das benutzerdefinierte Importtool ausschließt.

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

Wobei `ENTITY_CODE` der Wert ist, der für den Entitätsnamenparameter in der `import.xml` -Datei für das benutzerdefinierte Importtool verwendet wird.

## Verwandtes Lesen

[Konfigurieren Sie [!DNL cron] jobs](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) im Konfigurationshandbuch für den Adobe Commerce-Betrieb.
