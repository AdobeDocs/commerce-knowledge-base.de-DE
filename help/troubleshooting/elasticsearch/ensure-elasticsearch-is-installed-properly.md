---
title: Sicherstellen, dass das Elasticsearch ordnungsgemäß installiert ist
description: In diesem Artikel wird über Lösungen für Probleme gesprochen, die durch die fehlerhafte Installation und Konfiguration von Elasticsearch (ES) verursacht werden.
exl-id: d2c5971c-4db4-4857-ae79-970313bce981
feature: Install
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# Sicherstellen, dass das Elasticsearch ordnungsgemäß installiert ist

In diesem Artikel wird über Lösungen für Probleme gesprochen, die durch die fehlerhafte Installation und Konfiguration von Elasticsearch (ES) verursacht werden.

>[!WARNING]
>
>Beachten Sie bei Adobe Commerce auf Cloud-Infrastrukturen, dass Service-Upgrades nicht ohne Vorankündigung an unser Infrastrukturteam innerhalb von 48 Geschäftsstunden in die Produktionsumgebung verschoben werden können. Dies ist erforderlich, da wir sicherstellen müssen, dass wir einen Support-Techniker für die Infrastruktur zur Verfügung haben, der Ihre Konfiguration innerhalb eines gewünschten Zeitraums mit minimalen Ausfallzeiten in Ihrer Produktionsumgebung aktualisiert. 48 Stunden vor dem Zeitpunkt, zu dem Ihre Änderungen in der Produktion sein müssen, [ Sie ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), in dem Sie die erforderliche Service-Aktualisierung detailliert beschreiben und den Zeitpunkt angeben, zu dem der Upgrade-Prozess beginnen soll.

## Elasticsearch-Versionskompatibilität mit Adobe Commerce

* Adobe Commerce On-Premise und Adobe Commerce on Cloud Infrastructure:
   * v2.2.3+ unterstützt ES 5.x
   * v2.2.8+ und v2.3.1+ unterstützen ES 6.x
   * ES v2.x und v5.x werden aufgrund von [End of Life) nicht ](https://www.elastic.co/support/eol). Wenn Sie jedoch Adobe Commerce v2.3.1 haben und ES 2.x oder ES 5.x verwenden möchten, müssen Sie [den Elasticsearch-PHP-Client ändern](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/search/overview-search).
* Magento Open Source v2.3.0+ unterstützt ES 5.x und 6.x (6.x wird jedoch empfohlen).

## Problem

Die folgenden Symptome weisen darauf hin, dass das Elasticsearch nicht korrekt konfiguriert ist:

* `Error: No alive nodes in your cluster` - Dieser Fehler kann in den Adobe Commerce-Protokollen angezeigt werden:
   * `var/log/system.log`
   * `var/log/support_report.log`
   * `var/log/cron.log`
   * `var/log/exception.log`
   * oder in der Eingabeaufforderung (z. B. beim Ausführen einer Neuindizierung)
* Fehler, die darauf hinweisen, dass die Elasticsearch-Version nicht mit Ihrer aktuellen Version von Adobe Commerce kompatibel ist (dies ist ein für die Cloud-Infrastruktur spezifischer Adobe Commerce-Fehler):

  ```
  [YYYY-MM-DD HH:MM:SS] CRITICAL: Fix configuration with given suggestions:    - Elasticsearch version #<version> is not compatible with current version of magento    Upgrade elasticsearch version to ~5.0
  ```

Dabei *version* der Elasticsearch-Service, der in der Cloud-Umgebung ausgeführt wird.

## Ursache

Elasticsearch ist nicht ordnungsgemäß installiert. Dies kann folgende Ursachen haben:

* Ein Tippfehler in der Konfigurationsdatei.
* Eine Version in der Konfigurationsdatei, die mit keiner Version des Elasticsearchs übereinstimmt, das für die Umgebung installiert ist.
* Eine Version, die korrekt in der Umgebung installiert ist, korrekt in der Konfigurationsdatei konfiguriert ist, aber keine unterstützte Version für die derzeit installierte Version von Adobe Commerce ist.

## Lösung

So richten Sie das Elasticsearch korrekt ein:

* Händler, die mit Adobe Commerce in der Cloud-Infrastruktur arbeiten, können die Schritte in unserer Entwicklerdokumentation befolgen: [Einrichten des Elasticsearch-Service](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch).
* Händler, die Adobe Commerce On-Premise und Magento Open Source verwenden, können die Schritte in unserer Entwicklerdokumentation befolgen: [Installieren und Konfigurieren von Elasticsearch](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/search/overview-search).

Nachdem Sie das Elasticsearch eingerichtet haben, überprüfen Sie, ob es korrekt konfiguriert ist:

1. Melden Sie sich bei Ihrem -Server an.
1. Überprüfen Sie die Versionsnummer des Elasticsearchs (2.x, 5.x oder 6.x) in der Ausgabe des -Befehls, der ausgeführt wird: `curl -XGET <Elasticsearch hostname>:<Elasticsearch server port>` Beispiel in Adobe Commerce auf Cloud-Infrastruktur: `curl -XGET localhost:9200`
1. Überprüfen Sie, was in Adobe Commerce in der Cloud-Infrastrukturkonfiguration konfiguriert ist, indem Sie den Befehl ausführen: `php bin/magento config:show catalog/search`
1. Überprüfen Sie die `catalog/search/engine` und stellen Sie sicher, dass sie mit der Elasticsearch-Versionsnummer übereinstimmt. Zum Beispiel in Adobe Commerce auf Cloud-Infrastruktur:
   * Elasticsearch 5.x - elasticsearch5
   * Elasticsearch 6.x - elasticsearch6
   * Elasticsearch 2.x - elasticsearch
1. Überprüfen Sie `index_prefix`. Wenn Sie mehrere Umgebungen haben, stellen Sie sicher, dass Sie unterschiedliche `index_prefix` für sie haben.
