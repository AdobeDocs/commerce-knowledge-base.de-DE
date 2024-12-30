---
title: Die MySQL-Katalogsuchmaschine wird in Adobe Commerce 2.4.0 entfernt
description: Adobe Commerce On-Premises, Adobe Commerce on Cloud Infrastructure und Magento Open Source 2.4.0 werden in den nächsten Monaten veröffentlicht. Für Adobe Commerce On-Premise und Magento Open Source ist Version 2.4.0 Elasticsearch 6.x oder 7.x eine erforderliche Komponente, und MySQL-Suchmaschine wird entfernt. In Adobe Commerce ist in der Cloud-Infrastruktur bereits Elasticsearch erforderlich.
exl-id: 717be515-3cbf-42e9-9b72-caf11b8c3771
feature: Catalog Management, Search, Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---

# Die MySQL-Katalogsuchmaschine wird in Adobe Commerce 2.4.0 entfernt

Adobe Commerce On-Premises, Adobe Commerce on Cloud Infrastructure und Magento Open Source 2.4.0 werden in den nächsten Monaten veröffentlicht. Für Adobe Commerce On-Premise und Magento Open Source ist Version 2.4.0 Elasticsearch 6.x oder 7.x eine erforderliche Komponente, und MySQL-Suchmaschine wird entfernt. In Adobe Commerce ist in der Cloud-Infrastruktur bereits Elasticsearch erforderlich.

>[!WARNING]
>
>Wenn Sie Elasticsearch 6/7 nicht vor dem Upgrade installieren/konfigurieren, können ernsthafte Probleme mit Adobe Commerce auftreten. Bitte beachten Sie, dass Service-Upgrades auf Adobe Commerce in der Cloud-Infrastruktur erst nach einer Vorankündigung von 48 Geschäftsstunden an unser Infrastrukturteam in die Produktionsumgebung übertragen werden können. Dies ist erforderlich, da wir sicherstellen müssen, dass wir einen Support-Techniker für die Infrastruktur zur Verfügung haben, der Ihre Konfiguration innerhalb eines gewünschten Zeitraums mit minimalen Ausfallzeiten in Ihrer Produktionsumgebung aktualisiert. 48 Stunden vor dem Zeitpunkt, zu dem Ihre Änderungen in der Produktion vorgenommen werden müssen ([ ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)), wobei das erforderliche Service-Upgrade detailliert angegeben und der Zeitpunkt angegeben wird, zu dem das Upgrade gestartet werden soll.

Der Grund für die Entfernung der MySQL-Suchmaschine ist, dass Elasticsearch überlegene Suchfunktionen sowie eine Optimierung der Katalogleistung bietet.

## Betroffene Produkte und Versionen:

* Adobe Commerce On-Premise v2.4.0
* Magento Open Source v2.4.0

## Aktualisierung läuft:

<table style="height: 164px; width: 632.2px;">
<tbody>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;"><strong>Suchmaschine</strong></td>
<td class="wysiwyg-text-align-center" style="width: 478.2px;"><strong>Aktion</strong></td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">MySQL</td>
<td style="width: 478.2px;">Sie müssen Elasticsearch installieren. Siehe <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search">Installieren und Konfigurieren von Elasticsearch</a> in unserer Entwicklerdokumentation.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Elasticsearch (ohne aufgelistete Version)</td>
<td style="width: 478.2px;">Sie verwenden Elasticsearch 2 und müssen auf Elasticsearch 7 (empfohlen) oder 6 aktualisieren. Weitere Informationen finden Sie <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search#es-upgrade6">Upgrade </a> Elasticsearch und <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/configure-search-engine">Konfigurieren von Commerce für </a> Elasticsearch in unserer Entwicklerdokumentation.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">ELASTICSEARCH 5</td>
<td style="width: 478.2px;">Elasticsearch 5 hat das Ende <a href="https://www.elastic.co/support/eol"> Lebenszyklus erreicht </a> wird in Adobe Commerce 2.4.0 nicht mehr unterstützt. Aktualisierung auf Elasticsearch 7 (empfohlen) oder 6.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Elasticsearch 6 oder 7</td>
<td style="width: 478.2px;">Es sind keine zusätzlichen Schritte erforderlich, bevor Sie ein Upgrade auf Adobe Commerce 2.4.0 durchführen.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Drittanbietererweiterung</td>
<td style="width: 478.2px;">Sie müssen das Elasticsearch nicht installieren. Adobe Commerce empfiehlt, sich an den Suchmaschinenanbieter zu wenden, um festzustellen, ob Ihre Erweiterung vollständig mit Adobe Commerce 2.4.0 kompatibel ist.</td>
</tr>
</tbody>
</table>

## Installation:

Wenn Adobe Commerce On-Premise und Magento Open Source 2.4.0 veröffentlicht werden, ist Elasticsearch eine erforderliche Komponente. Daher müssen Sie vor der Installation von Version 2.4.0 einen Elasticsearch-Host einrichten und konfigurieren. Siehe [Installieren und Konfigurieren von Elasticsearch ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search) in unserer Entwicklerdokumentation.

Standardmäßig verwendet die Adobe Commerce-Suche Elasticsearch 7 als Suchmaschine und versucht, eine Verbindung zu einem Server unter localhost:9200 herzustellen. Elasticsearch 6.x wird ebenfalls unterstützt. Wenn Ihre Konfiguration nicht den Standardeinstellungen entspricht, können Sie diese Einstellungen mit Argumenten konfigurieren, die an `setup:install` übergeben werden, ähnlich wie bei der Konfiguration der Datenbankverbindung.

Beispiel: `setup:install --elasticsearch-host=es.mystore.com`

Während der Installation wird die Elasticsearch-Verbindung überprüft, und die Installation schlägt fehl, wenn Adobe Commerce keine Verbindung zu einem Elasticsearch-Host herstellen kann. Vergewissern Sie sich in diesem Fall, dass Ihr Elasticsearch betriebsbereit ist und Sie die richtigen Verbindungsparameter angegeben haben.
