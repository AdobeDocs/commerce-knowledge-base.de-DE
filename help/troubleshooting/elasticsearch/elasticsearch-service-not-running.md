---
title: Elasticsearch-Dienst wird nicht ausgeführt
description: Dieser Artikel bietet Lösungen für Fehler, die auftreten können, wenn der Elasticsearch-Service (ES) nicht ausgeführt wird (in der Regel infolge eines Absturzes). Zu den Symptomen können Fehler beim Ausführen von Konsistenzprüfungen mit curl, Neuindizierung mit der Befehlszeile, Fehler mit Ausnahme und PHP sowie Fehler auf Produktseiten gehören. In der Tabelle sind Fehler und Links zu Ressourcen aufgeführt, mit denen versucht werden soll, diese zu beheben. Ein Symptom kann verschiedene Ursachen haben.
exl-id: 2c2230de-cb30-4a03-8c3e-d9f44783dbae
source-git-commit: 3ff881f1c799201ed25ba9737864b1226d283c22
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# Elasticsearch-Dienst wird nicht ausgeführt

Dieser Artikel bietet Lösungen für Fehler, die auftreten können, wenn der Elasticsearch-Service (ES) nicht ausgeführt wird (in der Regel infolge eines Absturzes). Zu den Symptomen können Fehler beim Ausführen von Konsistenzprüfungen mit curl, Neuindizierung mit der Befehlszeile, Fehler mit Ausnahme und PHP sowie Fehler auf Produktseiten gehören. In der Tabelle sind Fehler und Links zu Ressourcen aufgeführt, mit denen versucht werden soll, diese zu beheben. Ein Symptom kann verschiedene Ursachen haben.

## Elasticsearch-Versionskompatibilität mit Adobe Commerce

* Adobe Commerce vor Ort und Adobe Commerce zur Cloud-Infrastruktur:

   * v2.2.3+ unterstützt ES 5.x
   * v2.2.8+ und v2.3.1+ unterstützen ES 6.x
   * ES v2.x und v5.x werden aufgrund von [Ende der Lebensdauer](https://www.elastic.co/support/eol). Wenn Sie jedoch über Adobe Commerce v2.3.1 verfügen und ES 2.x oder ES 5.x verwenden möchten, müssen Sie [Ändern des Elasticsearch-PHP-Clients](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-downgrade.html).

* Magento Open Source v2.3.0+ unterstützt ES 5.x und 6.x (es wird jedoch 6.x empfohlen).

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
<code>{"0":"{\"error\":{\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}]</code>
</td>
<td>
<a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsearch-5-is-configured-but-search-page-does-not-load-with-fielddata-is-disabled...-error.html">Elasticsearch 5 ist konfiguriert, die Suchseite wird jedoch nicht mit dem Fehler "Felddaten sind deaktiviert.."geladen.</a> in unserer Wissensdatenbank.
</td>
</tr>
<tr>
<td>
<code>Elasticsearch\Common\Exceptions\NoNodesAvailableException: Noticed exception 'Elasticsearch\Common\Exceptions\NoNodesAvailableException' with message 'No alive nodes found in your cluster' in /app/&lt;projectid&gt;/vendor/elasticsearch/elasticsearch/src/Elasticsearch/ConnectionPool/StaticNoPingConnectionPool.php:51</code>
</td>
<td>
Elasticsuite-Indizes werden nicht gelöscht.  Siehe <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.html">ElasticSuite-Trackingindizes verursachen Probleme mit Elasticsearch</a> in unserer Wissensdatenbank.
 </td>
</tr>
<tr>
<td>PHP-Fehler</td>
<td>
<i>Keine lebenden Knoten im Cluster gefunden","1":"#0 /app/&lt;projectid&gt;/vendor/elasticsearch/elasticsearch/src/Elasticsearch/Transport.php</i>
</td>
<td rowspan="4">
<ul>
<li>Ressourcen für ungenügenden Speicherplatz:<ul>
<li><a href="https://www.cyberciti.biz/datacenter/linux-unix-bsd-osx-cannot-write-to-hard-disk/">8 Tipps zur Lösung von Problemen mit Linux- und Unix-Systemfestplatten wie voll Disk Full oder kann nicht auf die Festplatte schreiben</a></li>
<li><a href="https://serverfault.com/questions/315181/df-says-disk-is-full-but-it-is-not">serverfailure: df sagt, dass die Festplatte voll ist, aber nicht</a></li>
<li><a href="https://unix.stackexchange.com/questions/125429/tracking-down-where-disk-space-has-gone-on-linux">unix.stackexchange.com: Verfolgen Sie, wo auf Linux Speicherplatz gegangen ist?</a></li>
<li>Protokolldateien werden nicht regelmäßig genug archiviert. Siehe <a href="https://docs.magento.com/m2/ee/user_guide/system/action-log-archive.html#configure-the-log-archive">Konfigurieren des Protokollarchivs</a> in unserer Entwicklerdokumentation.</li>
<li>Dateisystemordner sind nicht optimiert. Siehe <a href="https://docs.magento.com/m2/ee/user_guide/system/file-optimization.html">Dateioptimierung</a> in unserer Entwicklerdokumentation.</li>
<li>Wenn die Lösungen in der obigen Dokumentation das Problem nicht beheben, wenden Sie sich an Ihr Adobe-Account-Team, um zusätzlichen Speicher anzufordern.</li>
</ul>
</li>
<li>Wenn Ihr Datenträger nicht über genügend Speicherplatz verfügt, Sie aber dennoch die Fehlermeldungen in der linken Spalte erhalten, <a href="/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket">Support-Ticket einreichen</a>.</li>
</ul>
<ul>
<li>Siehe <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.html">ElasticSuite-Trackingindizes verursachen Probleme mit Elasticsearch</a> in unserer Wissensdatenbank.
</li>
</ul>
</td>
</tr>
<tr>
<td><code>Curl</code> error</td>
<td>Ausführen der <code>curl</code> -Befehl zum Überprüfen des Elasticsearch-Zustands:<code>curl -m1 localhost:9200/_cluster/health?pretty</code>(oder<code>curl -m1 elasticsearch.internal:9200/_cluster/health?pretty</code>für Starter-Konten) erzeugt diesen Fehler: <i>Fehler: curl: (7) Fehler bei Verbindung mit localhost port 9200: Verbindung verweigert</i> </td>
</tr>
<tr>
<td>Befehlszeilenfehler</td>
<td>Läuft <code>$ bin/magento indexer:reindex catalogsearch_fulltext</code> erzeugt diesen Fehler <i>Unbekannter Fehler beim Catalog Search-Indexprozess: Keine aktiven Knoten in Ihrem Cluster gefunden</i>
</td>
</tr>
<tr>
<td>Fehler auf Produktseiten
</td>
<td><i>Bei der Verarbeitung Ihrer Anfrage ist ein Fehler aufgetreten.
      Aus Sicherheitsgründen ist der Ausnahmedruck standardmäßig deaktiviert.</code></i>
</tr>
</table>
