---
title: ElasticSuite Trackingindizes verursacht Probleme mit dem Elasticsearch
description: In diesem Artikel wird über das Problem von Elasticsearch-Speicherproblemen gesprochen, die durch Tracking-Indizes verursacht werden, die vom ElasticSuite-Plug-in erzeugt werden.
exl-id: 67bfd06a-c801-4306-8510-a84a6fe5351a
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# ElasticSuite Trackingindizes verursacht Probleme mit dem Elasticsearch

>[!NOTE]
>
>ElasticSuite und die dazugehörigen Anwendungen sind Drittanbieter-Tools, die derzeit nicht von Adobe unterstützt werden. Diese Inhalte werden nur zu Informationszwecken und nicht als Hinweis darauf präsentiert, was für die Support-Abdeckung aktiviert ist.

In diesem Artikel wird über das Problem von Elasticsearch-Speicherproblemen gesprochen, die durch Tracking-Indizes verursacht werden, die vom ElasticSuite-Plug-in erzeugt werden.

## Betroffene Produkte und Versionen

ElasticSuite-Versionen vor 2.8.0 können Tracking-Indizes nicht regelmäßig bereinigen.

ElasticSuite-Versionen vor 2.9.8 / 2.10.7 speichern Tracking-Indizes in täglichen Indizes, was dazu führt, dass die Anzahl der offenen Indizes steigt.

## Problem

Wenn das ElasticSuite-Drittanbieter-Plug-in installiert ist, können Probleme mit dem Elasticsearch-Speicher auftreten, und der Elasticsearch-Service kann aufgrund von ElasticSuite-Trackingindizes abstürzen. Zu den Symptomen gehören:

* Elasticsearch stürzt ohne Speicherfehler ab.
* Beim Ausführen eines Health Command `curl -m1 localhost:9200/_cluster/health?pretty` oder `curl -m1 elasticsearch.internal:9200/_cluster/health?pretty` (für Starterkonten) gibt es Hunderte oder Tausende von `unassigned_shards`
* Die Leistung von Elasticsearch oder Websites wird stark beeinträchtigt.
* *Keine aktiven Knoten in Ihrem Cluster gefunden“* bei der Bereitstellung von Elasticsearch oder bei Protokollfehlern.
* *„Aktualisierung der Zuordnung zu [&lt;\*>_ tracking_log_event _&lt;\*>] wird abgelehnt“* bei Bereitstellungs- oder Protokollfehlern.

## Ursache

ElasticSuite verfügt über eine neue Funktion, die Tracking-Indizes erstellt. Diese Tracking-Indizes zeichnen auf, welche Suchbegriffe am häufigsten verwendet werden, welche Begriffe den meisten Umsatz generieren und welche Begriffe zu einer „Keine Ergebnisse“-Seite führen, damit Händler Synonyme erstellen können, um sie zu beheben. Die Trackingindizes werden anscheinend nicht gelöscht, sodass dem Elasticsearch die Ressourcen ausgehen und es zu Abstürzen kommt.

## Lösung

### Aktualisieren Sie Ihre ElasticSuite-Version, um Tracking-Indizes regelmäßig bereinigen zu können

Nachdem Sie das ElasticSuite-Plug-in auf eine höhere Version als 2.8.0 aktualisiert haben, können Sie eine regelmäßige Bereinigung der Indizes konfigurieren.

Navigieren Sie **Stores** > **Konfiguration** > **Tracking** > **Globale Konfiguration** > **Aufbewahrungsverzögerung**

Die standardmäßige Aufbewahrungsfrist beträgt 365 Tage. Sie können sie auf 30 oder 15 Tage reduzieren.

### Aktualisieren Sie Ihre ElasticSuite-Version, um monatliche statt tägliche Indizes zu verwenden

Nachdem Sie das ElasticSuite-Plug-in auf Version > 2.9.8 / 2.10.7 aktualisiert haben, basieren die Tracking-Indizes auf monatlicher Basis.

Sie können die Aufbewahrungsfrist dennoch verkürzen:

Navigieren Sie **Stores** > **Konfiguration** > **Tracking** > **Globale Konfiguration** > **Aufbewahrungsverzögerung**

Der standardmäßige Aufbewahrungszeitraum beträgt 12 Monate (führt zu 12 Indizes). Sie können sie auf 3 oder 6 Monate verkürzen.

### Bereinigung der Tracking-Indizes mit einem Cronjob

Erstellen Sie einen Cron-Auftrag, um die Tracking-Indizes zu löschen. Dieser Befehl löscht im letzten Monat erstellte Indizes:

```
   curl -XDELETE localhost:9200/<name in index> * **\_tracking\_log** * _$(date
    +'%Y%m' -d 'last month')*
```

Wenn Sie Indizes mit einer bestimmten Häufigkeit löschen möchten, erstellen Sie einen Cron-Auftrag, indem Sie die folgenden Artikel in unserer Entwicklerdokumentation lesen:

* [Konfigurieren eines benutzerdefinierten Cron-Auftrags und einer Cron-Gruppe (Tutorial)](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/crons/custom-cron-tutorial)
* [Richten Sie Cron-Aufträge ein](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property)
