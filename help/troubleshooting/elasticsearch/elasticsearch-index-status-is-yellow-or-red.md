---
title: Elasticsearch Index Status ist 'gelb' oder 'rot'
description: Der Artikel enthält eine Korrektur für den Fall, dass der Indexstatus des Elasticsearchs nicht "grün"lautet. '*gelb*' bezeichnet den Normalwert und '*rot*' zeigt den Fehler an. Der Status "gelb"oder "rot"kann im Zusammenhang mit fehlenden Produkten oder der Anzeige alter Produktinformationen auftreten.
exl-id: 27689511-6a41-41a9-8dda-a627d2f65263
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Elasticsearch Index Status ist &#39;gelb&#39; oder &#39;rot&#39;

>[!WARNING]
>
> [Die MySQL-Katalogsuchmaschine wird in Adobe Commerce 2.4.0 entfernt](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). Sie müssen den Elasticsearch-Host vor der Installation von Version 2.4.0 eingerichtet und konfiguriert haben. Siehe Abschnitt [Installieren und Konfigurieren von Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html).

Der Artikel enthält eine Fehlerbehebung für den Fall, dass der Indexstatus des Elasticsearchs nicht lautet *grün*&quot;. &#39;*gelb*&quot; bedeutet normal und &quot;*red*&quot; bedeutet &quot;Schlecht&quot;. Der Status &quot;gelb&quot;oder &quot;rot&quot;kann im Zusammenhang mit fehlenden Produkten oder der Anzeige alter Produktinformationen auftreten.

## Betroffene Versionen und Produkte

* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x
* Adobe Commerce On-Premise 2.2.x, 2.3.x

## Problem

Der Suchindex des Elasticsearch-Katalogs ist langsam, was zu einem Status von führt *gelb*&#39; or &#39;*red*&#39; anstelle von &#39;*grün*&quot;. Möglicherweise fehlen auch die Änderungen am Frontend.

## Ursache

Es kann mehrere mögliche Ursachen geben. Eine Ursache dafür ist, dass der Speicherplatz der Elasticsearch-Instanz ausgeht. Eine weitere Ursache sind doppelte Indizes.

## Lösung

Erstellen Sie eine neue mysql-Sicherungskopie, bevor Sie diese Schritte ausführen und sie außerhalb der Geschäftszeiten ausführen, um potenzielle Auswirkungen auf Ihre Kunden zu vermeiden:

1. Wechseln Sie vorübergehend zur MySQL-Suche - aktivieren Sie die MySQL-Suche. (Hinweis: Denken Sie daran, zu Elasticsearch zurückzukehren, da sonst Leistungsprobleme auftreten können.)
1. Führen Sie den folgenden Befehl aus, um duplizierte Indizes zu identifizieren:

   ```
   curl --silent -X GET localhost:9200/_cat/indices?v
   ```

1. So löschen Sie Indizes:

   ```
   curl -XDELETE localhost:9200/[your_index_name_here]
   ```

1. Elasticsearch erneut aktivieren.
1. Führen Sie eine vollständige Neuindizierung aus.
1. Überprüfen Sie den Indexstatus, indem Sie den folgenden Befehl ausführen:

   ```
   curl --silent -X GET localhost:9200/_cat/indices?v
   ```

Wenn diese Schritte nicht funktionieren, [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Verwandtes Lesen

Weitere Informationen finden Sie unter [Elasticsearch Cluster Health API](https://www.elastic.co/guide/en/elasticsearch/reference/current/cluster-health.html).
