---
title: Elasticsearch-Dienst nicht ausgeführt
description: Dieser Artikel enthält Lösungen für Fehler, die auftreten können, wenn der Elasticsearch (ES)-Service nicht ausgeführt wird (in der Regel als Folge eines Absturzes). Symptome können Fehler beim Ausführen von Konsistenzprüfungen mit curl, Neuindizierung über die Befehlszeile, Ausnahme- und PHP-Fehler sowie Fehler auf Produktseiten sein. In der Tabelle sind Fehler und Links zu Ressourcen aufgeführt, die nach einer Lösung suchen. Ein Symptom kann verschiedene Ursachen haben.
exl-id: 2c2230de-cb30-4a03-8c3e-d9f44783dbae
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# Elasticsearch-Dienst nicht ausgeführt

Dieser Artikel enthält Lösungen für Fehler, die auftreten können, wenn der Elasticsearch (ES)-Service nicht ausgeführt wird (in der Regel als Folge eines Absturzes). Symptome können Fehler beim Ausführen von Konsistenzprüfungen mit curl, Neuindizierung über die Befehlszeile, Ausnahme- und PHP-Fehler sowie Fehler auf Produktseiten sein. In der Tabelle sind Fehler und Links zu Ressourcen aufgeführt, die nach einer Lösung suchen. Ein Symptom kann verschiedene Ursachen haben.

## Elasticsearch-Versionskompatibilität mit Adobe Commerce

* Adobe Commerce On-Premise und Adobe Commerce on Cloud Infrastructure:

   * v2.2.3+ unterstützt ES 5.x
   * v2.2.8+ und v2.3.1+ unterstützen ES 6.x
   * ES v2.x und v5.x werden aufgrund von [End of Life) nicht ](https://www.elastic.co/support/eol). Wenn Sie jedoch Adobe Commerce v2.3.1 haben und ES 2.x oder ES 5.x verwenden möchten, müssen Sie [den Elasticsearch-PHP-Client ändern](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search).

* Magento Open Source v2.3.0+ unterstützt ES 5.x und 6.x (6.x wird jedoch empfohlen).

<table>
<tr>
<th>Symptome, wenn der ES-Dienst nicht ausgeführt wird</th>
<th>Details</th>
<th>Ressourcen</th>
</tr>
<tr>
<td rowspan="3">Ausnahmefehler</td>
</tr>
<tr>
<td>
<code>&lbrace;"0":"&lbrace;\"error\":&lbrace;\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}&rbrack;</code>
</td>
<td>
<a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsearch-5-is-configured-but-search-page-does-not-load-with-fielddata-is-disabled...-error.html">Elasticsearch 5 ist konfiguriert, aber die Suchseite wird nicht mit dem Fehler „Felddaten sind deaktiviert…“ </a> unserer Support-Wissensdatenbank geladen.
</td>
</tr>
<tr>
<td>
<code>Elasticsearch\Common\Exceptions\NoNodesAvailableException: Noticed exception 'Elasticsearch\Common\Exceptions\NoNodesAvailableException' with message 'No alive nodes found in your cluster' in /app/&lt;projectid&gt;/vendor/elasticsearch/elasticsearch/src/Elasticsearch/ConnectionPool/StaticNoPingConnectionPool.php:51</code>
</td>
<td>
Elasticsuite-Indizes werden nicht gelöscht.  Siehe <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.html">ElasticSuite Tracking-Indizes verursacht Probleme mit dem Elasticsearch </a> in unserer Support-Wissensdatenbank.
 </td>
</tr>
<tr>
<td>PHP-Fehler</td>
<td>
<i>Keine aktiven Knoten in Ihrem Cluster gefunden“,„1“:“#0 /app/&lt;projectid&gt;/vendor/elasticsearch/elasticsearch/src/Elasticsearch/Transport.php</i>
</td>
<td rowspan="4">
<ul>
<li>Ressourcen für unzureichenden Speicherplatz:<ul>
<li><a href="https://www.cyberciti.biz/datacenter/linux-unix-bsd-osx-cannot-write-to-hard-disk/">8 Tipps zur Lösung von Problemen mit der Festplatte von Linux- und Unix-Systemen, z. B. Volle Festplatte oder Schreibfehler auf der Festplatte</a></li>
<li><a href="https://serverfault.com/questions/315181/df-says-disk-is-full-but-it-is-not">Server-Fehler: DF gibt an, dass die Festplatte voll ist, dies ist aber nicht der Fall</a></li>
<li><a href="https://unix.stackexchange.com/questions/125429/tracking-down-where-disk-space-has-gone-on-linux">unix.stackexchange.com: Verfolgen Sie, wo Speicherplatz auf Linux verschwunden ist?</a></li>
<li>Protokolldateien werden nicht regelmäßig genug archiviert. Siehe <a href="https://experienceleague.adobe.com/en/docs/commerce-admin/systems/action-logs/action-log-archive">Konfigurieren des Protokollarchivs</a> in unserer Entwicklerdokumentation.</li>
<li>Dateien und Systemverzeichnisse sind nicht optimiert. Siehe <a href="https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/developer-tools#resource-file-optimization">Dateioptimierung</a> in unserer Entwicklerdokumentation.</li>
<li>Wenn die Lösungen in der obigen Dokumentation das Problem nicht lösen, sollten Sie sich an Ihr Adobe-Account-Team wenden, um zusätzlichen Speicher anzufordern.</li>
</ul>
</li>
<li>Wenn auf der Festplatte nicht genügend Speicherplatz vorhanden ist, die Fehlermeldungen jedoch weiterhin in der linken Spalte angezeigt werden, <a href="/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket"> Sie ein Support-Ticket </a>.</li>
</ul>
<ul>
<li>Siehe <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.html">ElasticSuite Tracking-Indizes verursacht Probleme mit dem Elasticsearch </a> in unserer Support-Wissensdatenbank.
</li>
</ul>
</td>
</tr>
<tr>
<td><code>Curl</code> Fehler</td>
<td>Das Ausführen des <code>curl</code>-Befehls zur Überprüfung des Elasticsearch-Zustands: <code>curl -m1 localhost:9200/_cluster/health?pretty</code>(oder<code>curl -m1 elasticsearch.internal:9200/_cluster/health?pretty</code>für Starterkonten) verursacht folgenden Fehler: <i>Fehler: curl: (7) Verbindung mit localhost-Port 9200 fehlgeschlagen: Verbindung verweigert</i> </td>
</tr>
<tr>
<td>Befehlszeilenfehler</td>
<td>Die Ausführung von <code>$ bin/magento indexer:reindex catalogsearch_fulltext</code> führt zu diesem Fehler <i>Unbekannter Katalogsuchindexierprozess-Fehler:
        Keine aktiven Knoten in Ihrem Cluster gefunden</i>
</td>
</tr>
<tr>
<td>Fehler auf Produktseiten
</td>
<td><i>Bei der Verarbeitung Ihrer Anfrage ist ein Fehler aufgetreten.
      Der Ausnahmedruck ist aus Sicherheitsgründen standardmäßig deaktiviert</code></i>
</tr>
</table>
