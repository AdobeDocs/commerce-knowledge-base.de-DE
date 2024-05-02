---
title: ElasticSuite-Trackingindizes verursachen Probleme mit Elasticsearch
description: In diesem Artikel wird das Problem der Speicherprobleme des Elasticsearchs beschrieben, die durch Tracking-Indizes verursacht werden, die vom ElasticSuite-Plug-in erstellt wurden.
exl-id: 67bfd06a-c801-4306-8510-a84a6fe5351a
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# ElasticSuite-Trackingindizes verursachen Probleme mit Elasticsearch

>[!NOTE]
>
>ElasticSuite und die zugehörigen Anwendungen sind Drittanbieter-Tools, die derzeit nicht von Adobe unterstützt werden. Dieser Inhalt wird nur als informativ und nicht als Hinweis darauf dargestellt, was für die Unterstützung möglich ist.

In diesem Artikel wird das Problem der Speicherprobleme des Elasticsearchs beschrieben, die durch Tracking-Indizes verursacht werden, die vom ElasticSuite-Plug-in erstellt wurden.

## Betroffene Produkte und Versionen

ElasticSuite-Versionen vor 2.8.0 können Tracking-Indizes nicht regelmäßig bereinigen.

ElasticSuite-Versionen vor 2.9.8 / 2.10.7 speichern Trackingindizes in täglichen Indizes, wodurch die Anzahl offener Indizes zunimmt.

## Problem

Wenn das Drittanbieter-Plug-in ElasticSuite installiert ist, treten möglicherweise Speicherprobleme mit dem Elasticsearch auf und der Elasticsearch-Dienst stürzt möglicherweise aufgrund von ElasticSuite-Trackingindizes ab. Zu den Symptomen gehören:

* Elasticsearch stürzt ohne Speicherfehler ab.
* Beim Ausführen eines &quot;Health&quot;-Befehls `curl -m1 localhost:9200/_cluster/health?pretty` oder `curl -m1 elasticsearch.internal:9200/_cluster/health?pretty` (für Starter-Konten) Hunderte oder Tausende von `unassigned_shards`
* Die Elasticsearch- oder Site-Performance ist stark beeinträchtigt.
* *&quot;Keine aktiven Knoten in Ihrem Cluster gefunden&quot;* im Elasticsearch-Bereitstellungs- oder Protokollfehler.
* *&quot;Verweigern des Mapping-Updates für [&lt;\*>_ tracking_log_event _&lt;\*>]&quot;* bei der Bereitstellung oder bei der Protokollierung von Fehlern.

## Ursache

ElasticSuite verfügt über eine neue Funktion, mit der Trackingindizes erstellt werden. In diesen Trackingindizes wird aufgezeichnet, welche Suchbegriffe am häufigsten verwendet werden, welche Begriffe den meisten Umsatz generieren und welche Begriffe zu einer Ergebnisseite führen, sodass Händler Synonyme erstellen können, um sie zu beheben. Die Tracking-Indizes werden offenbar nicht gelöscht, sodass Elasticsearch nicht über genügend Ressourcen verfügt und Abstürze feststellt.

## Lösung

### Aktualisieren Sie Ihre ElasticSuite-Version, um Tracking-Indizes regelmäßig bereinigen zu können.

Nachdem Sie das ElasticSuite-Plug-in auf Version höher als 2.8.0 aktualisiert haben, können Sie eine regelmäßige Bereinigung der Indizes konfigurieren.

Navigieren Sie zu **Stores** > **Konfiguration** > **Tracking** > **Globale Konfiguration** > **Bindungsverzögerung**

Der standardmäßige Aufbewahrungszeitraum beträgt 365 Tage. Sie können sie auf 30 oder 15 Tage reduzieren.

### Aktualisieren Sie Ihre ElasticSuite-Version, um monatliche Indizes anstelle täglicher Indizes zu verwenden.

Nachdem Sie das ElasticSuite-Plugin auf Version > 2.9.8 / 2.10.7 aktualisiert haben, basieren die Trackingindizes monatlich.

Sie können den Aufbewahrungszeitraum weiter verkürzen:

Navigieren Sie zu **Stores** > **Konfiguration** > **Tracking** > **Globale Konfiguration** > **Bindungsverzögerung**

Der standardmäßige Aufbewahrungszeitraum beträgt 12 Monate (generiert 12 Indizes). Sie können die Dosis auf 3 oder 6 Monate reduzieren.

### Verwenden eines Cronauftrags zum Bereinigen von Trackingindizes-Daten

Erstellen Sie einen Cron-Auftrag, um die Trackingindizes zu löschen. Mit diesem Befehl werden die im letzten Monat erstellten Indizes gelöscht:

```
   curl -XDELETE localhost:9200/<name in index> * **\_tracking\_log** * _$(date
    +'%Y%m' -d 'last month')*
```

Wenn Sie Indizes mit einer festgelegten Zeitfrequenz löschen möchten, erstellen Sie einen Cron-Auftrag, indem Sie in unserer Entwicklerdokumentation auf die folgenden Artikel verweisen:

* [Benutzerdefinierten Cron-Auftrag und eine Cron-Gruppe konfigurieren (Tutorial)](https://devdocs.magento.com/guides/v2.3/config-guide/cron/custom-cron-tut.html)
* [Einrichten von Cron-Aufträgen](https://devdocs.magento.com/guides/v2.3/cloud/configure/setup-cron-jobs.html)
