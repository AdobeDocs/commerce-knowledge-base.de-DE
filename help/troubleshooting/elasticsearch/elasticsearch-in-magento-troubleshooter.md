---
title: Elasticsearch in Adobe Commerce-Fehlerbehebung
description: Elasticsearch-Probleme in Adobe Commerce können mit dem Elasticsearch-Fehlerbehebungs-Tool gelöst werden. Klicken Sie auf jede Frage, um die Antwort in jedem Schritt der Problembehebung anzuzeigen.
exl-id: acae0da0-2918-4021-9fbe-c138940c5a72
feature: Categories
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 0%

---

# Elasticsearch in Adobe Commerce-Fehlerbehebung

Elasticsearch-Probleme in Adobe Commerce können mit dem Elasticsearch-Fehlerbehebungs-Tool gelöst werden. Klicken Sie auf jede Frage, um die Antwort in jedem Schritt der Problembehebung anzuzeigen.

>[!WARNING]
>
>Beachten Sie bei Adobe Commerce zur Cloud-Infrastruktur, dass Service-Upgrades nicht ohne 48-Stunden-Benachrichtigung an unser Infrastrukturteam in die Produktionsumgebung gesendet werden können. Dies ist erforderlich, da wir sicherstellen müssen, dass wir über einen Infrastruktur-Support-Mitarbeiter verfügen, der Ihre Konfiguration innerhalb eines gewünschten Zeitraums mit minimalen Ausfallzeiten in Ihrer Produktionsumgebung aktualisiert. 48 Stunden vor dem Zeitpunkt, zu dem Ihre Änderungen in der Produktion sein müssen [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) Geben Sie die erforderliche Dienstaktualisierung an und geben Sie den Zeitpunkt an, zu dem die Aktualisierung beginnen soll.

## Schritt 1: Auf Elasticsearch-Problem prüfen {#step-1}

+++**Könnten Sie sich mit Elasticsearch befassen?**

Elasticsearch-Probleme, die durch Fehlermeldungen angezeigt werden, &quot;_Keine aktiven Knoten im Cluster gefunden&quot;,_ fehlende Produkte und die Anzeige alter Produktinformationen.

a. JA - fahren Sie mit [Schritt 2](#step-2).\
b. NO - Suchen Sie erneut nach relevanten Suchbegriffen im [Wissensdatenbank zu Adobe Commerce Help Center](https://support.magento.com/hc).

+++

## Schritt 2: Auf Installationsproblem prüfen {#step-2}

+++**Ist es eine Neuinstallation von Elasticsearch?**

a. JA - [Stellen Sie sicher, dass Elasticsearch ordnungsgemäß installiert ist.](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) Überprüfen Sie außerdem, ob Sie sich in Adobe Commerce auf Cloud-Infrastruktur 2.3.1 oder höher befinden. Bei Merchants, die auf Adobe Commerce in der Cloud-Infrastruktur (ab Version 2.3.1) aktualisiert haben und eine Elasticsearch-Version vor 6.x verwenden, können bei der Bereitstellung Fehler auftreten. Um dieses Problem zu beheben, müssen das Elasticsearch-Client-Modul und der Elasticsearch-Dienst auf den neuesten empfohlenen Versionen basieren. Anweisungen hierzu finden Sie unter [Elasticsearch-Probleme nach Adobe Commerce auf der Cloud-Infrastruktur 2.3.1+](/help/troubleshooting/elasticsearch/elasticsearch-issues-after-magento-commerce-cloud-2-3-1-upgrade.md).\
b. NO - Überprüfen Sie den Zustand Ihres Clusters. Wenn Sie sich in einer Staging- oder Produktionsumgebung von Pro befinden, führen Sie diesen Befehl aus: `curl -m1 localhost:9200/_cluster/health?pretty`. Wenn Sie sich in einer Integrationsumgebung befinden (die alle Starter-Zweige enthält), führen Sie `curl -m1 elasticsearch.internal:9200/_cluster/health?pretty`. Fahren Sie mit [Schritt 3](#step-3).

+++

## Schritt 3: Überprüfen, ob Elasticsearch Cluster verfügbar ist {#step-3}

+++**Haben Sie eine Service-Antwort erhalten?**

a. JA - fahren Sie mit [Schritt 4](#step-4).\
b. NO - Fahren Sie mit [Schritt 9](#step-9).

+++

## Schritt 4: Überprüfen der Elasticsearch Cluster-Gesundheit {#step-4}

+++**Antwort grün?**

a. JA - Elasticsearch ist für die Verarbeitung von Daten verfügbar und die Neuindizierung sollte funktionieren. Fahren Sie mit [Schritt 5](#step-5).\
b. NO - Gelb oder rot bedeutet, dass es Probleme mit Verbindungen zwischen Knoten gibt und einige Daten möglicherweise nicht verfügbar sind. Wenn gelb, führen Sie den Befehl aus: `php bin/magento config:show catalog/search/engine` , um Ihre Suchmaschine zu überprüfen. Fahren Sie mit [Schritt 6](#step-6). Wenn rot, [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Schritt 5: Überprüfen der Suchfunktion {#step-5}

+++**Suchproblem?**

Zu den Symptomen gehören möglicherweise keine Produkte, leere Kategorien oder keine Aktualisierungen der Produkte oder Produktkategorien sind nicht korrekt.

a. YES - Führen Sie diesen Befehl aus, um den Status der Katalogsuche zu überprüfen: `php bin/magento indexer:status`. Fahren Sie mit [Schritt 8](#step-8).\
b. NO - Befehl ausführen: `php bin/magento config:show catalog/search/engine`. Fahren Sie mit [Schritt 6](#step-6).

+++

## Schritt 6: Überprüfen der ElasticSuite {#step-6}

+++**ElasticSuite in Verwendung?**

a. YES - Überprüfen Sie, ob sich die ElasticSuite in der aktuellen Version befindet, indem Sie diesen Befehl ausführen: `cat composer.lock | grep -A 1 elasticsuite | grep '"version"'` Informationen dazu, ob diese Version abgeschrieben oder empfohlen wird, finden Sie unter [Github: Smile-SA/elaticsuite](https://github.com/Smile-SA/elasticsuite). Wenn ElasticSuite auf dem neuesten Stand ist, fahren Sie mit [Schritt 10](#step-10).\
b. NO - fahren Sie mit [Schritt 7](#step-7).

+++

## Schritt 7: Überprüfen der aktuellen ECE-Tools {#step-7}

+++**Ist ECE-Tools die neueste Version?**

Führen Sie den Befehl aus: `php ./vendor/bin/ece-tools -V` und überprüfen Sie die ECE-Tools-Version. Ist es das [aktuelle Version der ECE-Tools](https://github.com/magento/ece-tools/releases)?

a. JA - fahren Sie mit [Schritt 5a](#step-5).\
b. NO - Upgrade der ECE-Tools auf die neueste Version. Führen Sie den Befehl aus `php bin/magento config: show catalog/search/engine` , um Ihre Suchmaschine zu überprüfen. Fahren Sie mit [Schritt 6](#step-6).

+++

## Schritt 8: Auf Neuindizierung prüfen {#step-8}

+++**Ist der Status der Katalogsuche in _Verarbeitung_?**

a. YES - Sie müssen warten, bis die Verarbeitung abgeschlossen ist, und dann überprüfen, ob die Produktkategorien aktualisiert wurden. Falls nicht, [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Wenn der Status der Katalogsuche _Neu indizieren_ in CLI/Terminal ausgeführt werden: `php bin/magento cron:run`. Wenn dies nicht funktioniert, führen Sie Folgendes aus: `php bin/magento indexer:reindex`. Wenn dies das Problem nicht behebt, [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Schritt 9: Überprüfen der YAML-Konfiguration {#step-9}

+++**`.yaml`Datei kürzlich aktualisiert?**

a. JA - Prüfung `.yaml` Elasticsearch-Konfiguration durch Verweis auf DevDocs [Einrichten des Elasticsearchs: Aktivieren des Elasticsearchs](https://devdocs.magento.com/cloud/project/project-conf-files_services-elastic.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=elastic%20search%20yaml).\
b. NO - [Support-Ticket senden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Schritt 10: Überprüfen auf Trackingindizes {#step-10}

+++**Gibt es Trackingindizes?**

Ausführen `curl elasticsearch.internal:9200/_cat/indices` (wenn Sie sich in einer Integrationsumgebung befinden, die alle Starter-Zweige enthält). Wenn Sie die Staging- oder Produktionsumgebung von Pro verwenden, starten Sie `curl localhost:9200/_cat/indices`. Gibt es Trackingindizes? Überprüfen Sie die Ausgabe auf`_tracking_log_`.

a. JA - Wenn Sie eine Version der ElasticSuite vor Version 2.8.0 verwenden, wird empfohlen, dass Sie [Aktualisierung auf ElasticSuite 2.8.0, um die Beibehaltung von Trackingindizes anzupassen oder Tracking zu deaktivieren](https://support.magento.com/hc/en-us/articles/360035266131?). Wenn Sie nicht sofort eine Aktualisierung durchführen können, können Sie [Erstellen eines Crons zum Entfernen von Trackingindizes](/help/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.md). Dies kann jedoch zu Leistungsproblemen führen. Führen Sie nach dem Upgrade auf ElasticSuite 2.8.0 oder Entfernen der Trackingindizes den Befehl aus (wenn Sie sich in der Staging- oder Produktionsumgebung von Pro befinden):`localhost:9200/_cat/allocation?v` , um den verfügbaren Speicherplatz zu überprüfen. Wenn Sie sich in einer der Integrationsumgebungen befinden (die alle Starter-Zweige enthalten), führen Sie die `elasticsearch.internal:9200/_cat/allocation?v`. Fahren Sie mit [Schritt 11](#step-11).\
b. NO - Wenn Sie die Pro-Staging- oder Produktionsumgebungen ausführen `localhost:9200/_cat/allocation?v` und überprüfen Sie den verfügbaren Speicherplatz. Wenn Sie sich in einer der Integrationsumgebungen befinden (die alle Starter-Zweige enthalten), führen Sie die `elasticsearch.internal:9200/_cat/allocation?v`. Fahren Sie mit [Schritt 11](#step-11).

+++

## Schritt 11: Bestimmten Fehler nachschlagen {#step-11}

+++**Spezifischer Fehler?**

Adobe Commerce- und ES-Protokolle, Erweiterungen und benutzerdefinierter Code.

a. JA - Lesen Sie den Artikel &quot;Adobe Commerce Help Center - Fehlerbehebung&quot;. [Sicherstellen, dass Elasticsearch ordnungsgemäß installiert ist](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) oder [Elasticsearch stürzt ab oder weist bei Verwendung des ElasticSuite-Plug-ins Speicherprobleme auf](https://support.magento.com/hc/en-us/articles/360035266131).\
b. NO - Fahren Sie mit [Schritt 12](#step-12).

+++

## Schritt 12: Überprüfen des verfügbaren Speichers {#step-12}

+++**Speichernutzung > 85 %?**

a. JA - Sie müssen den verfügbaren Speicher erhöhen. Siehe DevDocs .[Einrichten des Elasticsearchs: Aktivieren des Elasticsearchs](https://devdocs.magento.com/cloud/project/project-conf-files_services-elastic.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=elastic%20search%20yaml). Führen Sie dann Folgendes aus: `localhost:9200/_cat/allocation?v` (wenn Sie Staging- oder Produktionsumgebungen von Pro verwenden). Wenn Sie sich in einer der Integrationsumgebungen befinden (die alle Starter-Zweige enthalten), führen Sie Folgendes aus: `elasticsearch.internal:9200/_cat/allocation?v`. Fahren Sie mit [Schritt 11](#step-11).\
b. NO - [Support-Ticket senden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Zurück zu Schritt 1](#step-1)
