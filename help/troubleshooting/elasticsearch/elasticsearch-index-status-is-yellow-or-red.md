---
title: Elasticsearch-Indexstatus ist 'gelb' oder 'rot'
description: Der Artikel bietet eine Fehlerbehebung für den Fall, dass der Elasticsearch-Indexstatus nicht "*grün*" ist. '*gelb*' bedeutet normal, und '*rot*' bedeutet schlecht. Der Status „gelb“ oder „rot“ kann in Verbindung mit fehlenden Produkten oder der Anzeige alter Produktinformationen auftreten.
exl-id: 27689511-6a41-41a9-8dda-a627d2f65263
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Elasticsearch-Indexstatus ist &#39;gelb&#39; oder &#39;rot&#39;

>[!WARNING]
>
> [Die MySQL-Katalogsuchmaschine wird in Adobe Commerce 2.4.0 entfernt](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). Vor der Installation von Version 2.4.0 müssen Sie den Elasticsearch-Host eingerichtet und konfiguriert haben. Siehe [Installieren und Konfigurieren von Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search).

Der Artikel bietet eine Fehlerbehebung für den Fall, dass der Elasticsearch-Indexstatus nicht &quot;*&quot;*. &quot;*gelb*&quot; bedeutet „normal“ und &quot;*rot* bedeutet „schlecht“. Der Status „gelb“ oder „rot“ kann in Verbindung mit fehlenden Produkten oder der Anzeige alter Produktinformationen auftreten.

## Betroffene Versionen und Produkte

* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x
* Adobe Commerce On-Premise 2.2.x, 2.3.x

## Problem

Der Suchindex für den Elasticsearch-Katalog ist langsam, was zu einem Status von &quot;*gelb*&quot; oder &quot;*rot*&quot; anstelle von &quot;*grün*&quot; führt. Möglicherweise treten auch fehlende Änderungen im Frontend auf.

## Ursache

Es kann mehrere potenzielle Ursachen geben. Ein Grund dafür ist, dass der Elasticsearch-Instanz der Speicherplatz ausgeht. Eine weitere Ursache sind doppelte Indizes.

## Lösung

Erstellen Sie einen neuen MySQL-Dump, bevor Sie diese Schritte ausführen, und führen Sie sie außerhalb der Geschäftszeiten durch, um eine mögliche Beeinträchtigung Ihrer Kunden zu vermeiden:

1. Temporär zur MySQL-Suche wechseln - Aktivieren Sie die MySQL-Suche. (Hinweis: Denken Sie daran, zum Elasticsearch zurückzukehren, da andernfalls Leistungsprobleme auftreten können.)
1. Um doppelte Indizes zu identifizieren, führen Sie den folgenden Befehl aus:

   ```
   curl --silent -X GET localhost:9200/_cat/indices?v
   ```

1. So löschen Sie Indizes:

   ```
   curl -XDELETE localhost:9200/[your_index_name_here]
   ```

1. Elasticsearch erneut aktivieren.
1. Führen Sie eine vollständige Neuindizierung durch.
1. Überprüfen Sie den Indexstatus, indem Sie den folgenden Befehl ausführen:

   ```
   curl --silent -X GET localhost:9200/_cat/indices?v
   ```

Wenn diese Schritte nicht funktionieren, [ein Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Verwandtes Lesen

Weitere Informationen finden Sie unter [Elasticsearch Cluster Health API](https://www.elastic.co/guide/en/elasticsearch/reference/current/cluster-health.html).
