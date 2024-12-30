---
title: Elasticsearch in Adobe Commerce - Fehlerbehebung
description: Elasticsearch-Probleme in Adobe Commerce können mit dem Tool zur Elasticsearch-Fehlerbehebung behoben werden. Klicken Sie auf die einzelnen Fragen, um die Antwort in jedem Schritt der Fehlerbehebung anzuzeigen.
exl-id: acae0da0-2918-4021-9fbe-c138940c5a72
feature: Categories
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 0%

---

# Elasticsearch in Adobe Commerce - Fehlerbehebung

Elasticsearch-Probleme in Adobe Commerce können mit dem Tool zur Elasticsearch-Fehlerbehebung behoben werden. Klicken Sie auf die einzelnen Fragen, um die Antwort in jedem Schritt der Fehlerbehebung anzuzeigen.

>[!WARNING]
>
>Beachten Sie bei Adobe Commerce auf Cloud-Infrastrukturen, dass Service-Upgrades nicht ohne Vorankündigung an unser Infrastrukturteam innerhalb von 48 Geschäftsstunden in die Produktionsumgebung verschoben werden können. Dies ist erforderlich, da wir sicherstellen müssen, dass wir einen Support-Techniker für die Infrastruktur zur Verfügung haben, der Ihre Konfiguration innerhalb eines gewünschten Zeitraums mit minimalen Ausfallzeiten in Ihrer Produktionsumgebung aktualisiert. 48 Stunden vor dem Zeitpunkt, zu dem Ihre Änderungen in der Produktion vorgenommen werden müssen ([ ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)), wobei das erforderliche Service-Upgrade detailliert angegeben und der Zeitpunkt angegeben wird, zu dem das Upgrade gestartet werden soll.

## Schritt 1: Prüfen auf Elasticsearch-Probleme {#step-1}

+++**Könnte Ihr Problem mit dem Elasticsearch zusammenhängen?**

Elasticsearch-Probleme werden durch Fehlermeldungen, &quot;_Keine in Ihrem Cluster gefundenen aktiven Knoten“,_ fehlender Produkte und die Anzeige alter Produktinformationen angezeigt.

a. JA - Mit [Schritt 2](#step-2) fortfahren.\
b. NEIN - Suchen Sie erneut nach relevanten Suchbegriffen in der [Adobe Commerce Help Center Knowledge Base](https://support.magento.com/hc).

+++

## Schritt 2: Überprüfen des Installationsproblems {#step-2}

+++**Ist es eine Neuinstallation von Elasticsearch?**

a. JA - [Sicherstellen, dass das Elasticsearch ordnungsgemäß installiert ist.](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) Überprüfen Sie auch, ob Sie Adobe Commerce unter Cloud-Infrastruktur 2.3.1 oder höher verwenden. Händler, die auf Adobe Commerce in der Cloud-Infrastruktur (Version 2.3.1 und höher) aktualisiert haben und eine Version von Elasticsearch vor 6.x verwenden, können bei der Bereitstellung Fehler auftreten. Um dieses Problem zu beheben, müssen das Elasticsearch-Client-Modul und der Elasticsearch-Service die neuesten empfohlenen Versionen verwenden. Anweisungen hierzu finden Sie unter [Elasticsearch-Probleme nach einem Upgrade von Adobe Commerce auf Cloud-Infrastruktur 2.3.1 oder höher](/help/troubleshooting/elasticsearch/elasticsearch-issues-after-magento-commerce-cloud-2-3-1-upgrade.md).\
b. NEIN - Überprüfen Sie den Zustand Ihres Clusters. Wenn Sie sich in einer Pro-Staging- oder Produktionsumgebung befinden, führen Sie diesen Befehl aus: `curl -m1 localhost:9200/_cluster/health?pretty`. Wenn Sie sich in einer Integrationsumgebung befinden (die alle Starter-Verzweigungen umfasst), führen Sie `curl -m1 elasticsearch.internal:9200/_cluster/health?pretty` aus. Fahren Sie mit [Schritt 3](#step-3) fort.

+++

## Schritt 3: Überprüfen, ob ein Elasticsearch-Cluster verfügbar ist {#step-3}

+++**Haben Sie eine Service-Antwort erhalten?**

a. JA - Mit [Schritt 4](#step-4) fortfahren.\
b. NEIN - Fahren Sie mit [Schritt 9](#step-9) fort.

+++

## Schritt 4: Überprüfen Sie, ob der Elasticsearch-Cluster fehlerfrei ist. {#step-4}

+++**Antwort grün?**

a. JA - Das Elasticsearch ist für die Verarbeitung von Daten verfügbar und die Neuindizierung sollte funktionieren. Fahren Sie mit [Schritt 5](#step-5) fort.\
b. NEIN - Gelb oder rot bedeutet, dass es Probleme mit Verbindungen zwischen Knoten gibt und einige Daten nicht verfügbar sind. Wenn gelb, führen Sie den Befehl: `php bin/magento config:show catalog/search/engine` aus, um Ihre Suchmaschine zu überprüfen. Fahren Sie mit [Schritt 6](#step-6) fort. Wenn rot, [ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Schritt 5: Überprüfen, ob die Suche funktioniert {#step-5}

+++**Suchanfrage?**

Symptome können sein, dass keine Produkte, leeren Kategorien oder keine Aktualisierungen von Produkten oder Produktkategorien nicht korrekt sind.

a. JA - Führen Sie diesen Befehl aus, um den Status der Katalogsuche zu überprüfen: `php bin/magento indexer:status`. Fahren Sie mit [Schritt 8](#step-8) fort.\
b. NEIN - Befehl ausführen: `php bin/magento config:show catalog/search/engine`. Fahren Sie mit [Schritt 6](#step-6) fort.

+++

## 6. Schritt - ElasticSuite prüfen {#step-6}

+++**ElasticSuite im Einsatz?**

a. JA - Überprüfen Sie, ob ElasticSuite die aktuelle Version aufweist, indem Sie diesen Befehl ausführen: `cat composer.lock | grep -A 1 elasticsuite | grep '"version"'` Informationen dazu, ob diese Version veraltet oder empfohlen ist, finden Sie unter [Github: Smile-SA/elaticsuite](https://github.com/Smile-SA/elasticsuite). Wenn ElasticSuite aktuell ist, fahren Sie mit [Schritt 10](#step-10) fort.\
b. NEIN - mit [Schritt 7](#step-7) fortfahren.

+++

## Schritt 7 - ECE-Tools auf dem neuesten Stand überprüfen {#step-7}

+++**Ist ECE-tools die neueste Version?**

Führen Sie den Befehl `php ./vendor/bin/ece-tools -V` aus und überprüfen Sie die Version der ECE-Tools. Ist es die [neueste Version der ECE-Tools](https://github.com/magento/ece-tools/releases)?

a. JA - Mit [Schritt 5a](#step-5) fortfahren.\
b. NEIN - Aktualisieren Sie ECE-Tools auf die neueste Version. Führen Sie den Befehl `php bin/magento config: show catalog/search/engine` aus, um Ihre Suchmaschine zu überprüfen. Fahren Sie mit [Schritt 6](#step-6) fort.

+++

## Schritt 8 - Auf Neuindizierung prüfen {#step-8}

+++**Ist der Status der Katalogsuche in _Verarbeitung_?**

a. JA - Sie müssen warten, bis die Verarbeitung abgeschlossen ist, und dann überprüfen, ob die Produktkategorien aktualisiert wurden. Andernfalls reichen [ein Support-Ticket ein](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NEIN - Wenn der Status der Katalogsuche &quot;_erforderlich“ lautet_ führen Sie in CLI/Terminal `php bin/magento cron:run` aus. Wenn dies nicht funktioniert, führen Sie Folgendes aus: `php bin/magento indexer:reindex`. Wenn sich das Problem hierdurch nicht beheben lässt, [ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Schritt 9: Überprüfen der YAML-Konfiguration {#step-9}

+++**`.yaml`Datei kürzlich aktualisiert?**

a. JA - Überprüfen Sie `.yaml` Elasticsearch-Konfiguration unter „DevDocs“ [Elasticsearch einrichten: , um das Elasticsearch zu aktivieren](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch).\
b. NEIN - [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Schritt 10: Prüfen auf Tracking-Indizes {#step-10}

+++**Gibt es Trackingindizes?**

Führen Sie `curl elasticsearch.internal:9200/_cat/indices` aus (wenn Sie sich in einer Integrationsumgebung befinden, die alle Starter-Verzweigungen enthält). Wenn Sie sich in der Pro-Staging- oder Produktionsumgebung befinden, führen Sie `curl localhost:9200/_cat/indices` aus. Gibt es Tracking-Indizes? Überprüfen Sie die Ausgabe für`_tracking_log_`.

a. JA - Wenn Sie eine Version von ElasticSuite vor Version 2.8.0 verwenden, wird empfohlen, dass Sie [auf ElasticSuite 2.8.0 aktualisieren, um die Beibehaltung von Tracking-Indizes anzupassen oder das Tracking zu deaktivieren](https://support.magento.com/hc/en-us/articles/360035266131?). Wenn Sie nicht sofort aktualisieren können, können Sie [einen Cron erstellen, um Trackingindizes zu entfernen](/help/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.md). Dies kann jedoch zu Leistungsproblemen führen. Nachdem Sie ein Upgrade auf ElasticSuite 2.8.0 durchgeführt oder Tracking-Indizes entfernt haben, führen Sie den Befehl aus (wenn Sie sich in Pro-Staging- oder Produktionsumgebungen befinden): `localhost:9200/_cat/allocation?v`, um den verfügbaren Speicherplatz zu überprüfen. Wenn Sie sich in einer der Integrationsumgebungen befinden (die alle Starter-Verzweigungen umfasst), führen Sie `elasticsearch.internal:9200/_cat/allocation?v` aus. Fahren Sie mit [Schritt 11](#step-11) fort.\
b. NEIN - Wenn Sie sich in Pro-Staging- oder Produktionsumgebungen befinden, führen Sie `localhost:9200/_cat/allocation?v` aus und überprüfen Sie den verfügbaren Speicherplatz. Wenn Sie sich in einer der Integrationsumgebungen befinden (die alle Starter-Verzweigungen umfasst), führen Sie `elasticsearch.internal:9200/_cat/allocation?v` aus. Fahren Sie mit [Schritt 11](#step-11) fort.

+++

## Schritt 11: Spezifischen Fehler nachschlagen {#step-11}

+++**Spezifischer Fehler?**

Adobe Commerce- und ES-Protokolle, Erweiterungen und benutzerdefinierter Code.

A. JA - Lesen Sie den Artikel zur Fehlerbehebung im Adobe Commerce Help Center [Stellen Sie sicher, dass das Elasticsearch ordnungsgemäß installiert ist](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) oder das [Elasticsearch abstürzt oder bei der Verwendung des ElasticSuite-Plug-ins Probleme mit dem Arbeitsspeicher auftreten](https://support.magento.com/hc/en-us/articles/360035266131).\
b. NEIN - Mit [Schritt 12](#step-12) fortfahren.

+++

## Schritt 12: Überprüfen des verfügbaren Speichers {#step-12}

+++**Speicherauslastung > 85 %?**

a. JA - Sie müssen den verfügbaren Speicher erhöhen. Siehe DevDocs-[ Elasticsearch: So aktivieren Sie das Elasticsearch ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch). Führen Sie dann Folgendes aus: `localhost:9200/_cat/allocation?v` (wenn Sie sich in Pro-Staging- oder Produktionsumgebungen befinden). Wenn Sie sich in einer der Integrationsumgebungen befinden (die alle Starter-Verzweigungen umfasst), führen Sie `elasticsearch.internal:9200/_cat/allocation?v` aus. Fahren Sie mit [Schritt 11](#step-11) fort.\
b. NEIN - [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Zurück zu Schritt 1](#step-1)
