---
title: Sicherstellen, dass Elasticsearch ordnungsgemäß installiert ist
description: In diesem Artikel werden Lösungen für Probleme beschrieben, die durch fehlerhafte Installation und Konfiguration von Elasticsearch (ES) verursacht werden.
exl-id: d2c5971c-4db4-4857-ae79-970313bce981
feature: Install
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# Sicherstellen, dass Elasticsearch ordnungsgemäß installiert ist

In diesem Artikel werden Lösungen für Probleme beschrieben, die durch fehlerhafte Installation und Konfiguration von Elasticsearch (ES) verursacht werden.

>[!WARNING]
>
>Beachten Sie bei Adobe Commerce zur Cloud-Infrastruktur, dass Service-Upgrades nicht ohne 48-Stunden-Benachrichtigung an unser Infrastrukturteam in die Produktionsumgebung gesendet werden können. Dies ist erforderlich, da wir sicherstellen müssen, dass wir über einen Infrastruktur-Support-Mitarbeiter verfügen, der Ihre Konfiguration innerhalb eines gewünschten Zeitraums mit minimalen Ausfallzeiten in Ihrer Produktionsumgebung aktualisiert. 48 Stunden vor dem Zeitpunkt, zu dem Ihre Änderungen in der Produktion sein müssen, [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) Geben Sie die erforderliche Dienstaktualisierung an und geben Sie den Zeitpunkt an, zu dem die Aktualisierung beginnen soll.

## Elasticsearch-Versionskompatibilität mit Adobe Commerce

* Adobe Commerce vor Ort und Adobe Commerce zur Cloud-Infrastruktur:
   * v2.2.3+ unterstützt ES 5.x
   * v2.2.8+ und v2.3.1+ unterstützen ES 6.x
   * ES v2.x und v5.x werden aufgrund von [Ende der Lebensdauer](https://www.elastic.co/support/eol). Wenn Sie jedoch über Adobe Commerce v2.3.1 verfügen und ES 2.x oder ES 5.x verwenden möchten, müssen Sie [Ändern des Elasticsearch-PHP-Clients](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-downgrade.html).
* Magento Open Source v2.3.0+ unterstützt ES 5.x und 6.x (es wird jedoch 6.x empfohlen).

## Problem

Die folgenden Symptome zeigen, dass Elasticsearch nicht richtig konfiguriert ist:

* `Error: No alive nodes in your cluster` - Dieser Fehler kann in Adobe Commerce-Protokollen angezeigt werden:
   * `var/log/system.log`
   * `var/log/support_report.log`
   * `var/log/cron.log`
   * `var/log/exception.log`
   * oder in der Eingabeaufforderung (z. B. beim Ausführen einer Neuindizierung)
* Fehler, die darauf hinweisen, dass die Elasticsearch-Version nicht mit Ihrer aktuellen Version von Adobe Commerce kompatibel ist (dies ist ein Adobe Commerce-Fehler, der eine Cloud-Infrastruktur-spezifische Fehlermeldung enthält):

  ```
  [YYYY-MM-DD HH:MM:SS] CRITICAL: Fix configuration with given suggestions:    - Elasticsearch version #<version> is not compatible with current version of magento    Upgrade elasticsearch version to ~5.0
  ```

Wo *version* ist der Elasticsearch-Dienst, der in der Cloud-Umgebung ausgeführt wird.

## Ursache

Elasticsearch ist nicht ordnungsgemäß installiert. Dies könnte folgende Gründe haben:

* Ein Tippfehler in der Konfigurationsdatei.
* Eine Version in der Konfigurationsdatei, die mit keiner Version des für die Umgebung installierten Elasticsearchs übereinstimmt.
* Eine Version, die ordnungsgemäß in der Umgebung installiert und in der Konfigurationsdatei korrekt konfiguriert ist, aber keine unterstützte Version für die derzeit installierte Version von Adobe Commerce ist.

## Lösung

So richten Sie Elasticsearch ordnungsgemäß ein:

* Merchandising in Adobe Commerce in der Cloud-Infrastruktur kann den Schritten in unserer Entwicklerdokumentation folgen: [Elasticsearch-Dienst einrichten](https://devdocs.magento.com/guides/v2.3/cloud/project/project-conf-files_services-elastic.html).
* Händler in Adobe Commerce vor Ort und Magento Open Source können die Schritte in unserer Entwicklerdokumentation befolgen: [Installieren und Konfigurieren von Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html).

Nachdem Sie Elasticsearch eingerichtet haben, überprüfen Sie, ob es korrekt konfiguriert ist:

1. Melden Sie sich bei Ihrem Server an.
1. Überprüfen Sie die Versionsnummer des Elasticsearchs (2.x, 5.x oder 6.x) in der Ausgabe der Ausführung des Befehls: `curl -XGET <Elasticsearch hostname>:<Elasticsearch server port>` Beispiel: In Adobe Commerce in der Cloud-Infrastruktur: `curl -XGET localhost:9200`
1. Überprüfen Sie, was in Adobe Commerce in der Cloud-Infrastrukturkonfiguration konfiguriert ist, indem Sie den Befehl ausführen: `php bin/magento config:show catalog/search`
1. Überprüfen `catalog/search/engine` und stellen Sie sicher, dass sie mit der Versionsnummer des Elasticsearchs übereinstimmt. Beispiel: In Adobe Commerce in der Cloud-Infrastruktur:
   * Elasticsearch 5.x - elasticsearch5
   * Elasticsearch 6.X - elasticsearch6
   * Elasticsearch 2.X - Elasticsearch
1. Überprüfen `index_prefix`. Wenn Sie mehrere Umgebungen haben, stellen Sie sicher, dass Sie unterschiedliche `index_prefix` -Werte.
