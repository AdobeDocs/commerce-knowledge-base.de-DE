---
title: Die MySQL-Katalogsuchmaschine wird in Adobe Commerce 2.4.0 entfernt
description: Adobe Commerce vor Ort, Adobe Commerce über Cloud-Infrastruktur und Magento Open Source 2.4.0 werden in den kommenden Monaten veröffentlicht. Für Adobe Commerce On-Premise und Magento Open Source Version 2.4.0 ist Elasticsearch 6.x oder 7.x erforderlich und die MySQL-Suchmaschine wird entfernt. In Adobe Commerce ist für Cloud-Infrastruktur bereits Elasticsearch erforderlich.
exl-id: 717be515-3cbf-42e9-9b72-caf11b8c3771
feature: Catalog Management, Search, Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---

# Die MySQL-Katalogsuchmaschine wird in Adobe Commerce 2.4.0 entfernt

Adobe Commerce vor Ort, Adobe Commerce über Cloud-Infrastruktur und Magento Open Source 2.4.0 werden in den kommenden Monaten veröffentlicht. Für Adobe Commerce On-Premise und Magento Open Source Version 2.4.0 ist Elasticsearch 6.x oder 7.x erforderlich und die MySQL-Suchmaschine wird entfernt. In Adobe Commerce ist für Cloud-Infrastruktur bereits Elasticsearch erforderlich.

>[!WARNING]
>
>Wenn Sie Elasticsearch 6/7 nicht installieren/konfigurieren, bevor Sie versuchen, ein Upgrade durchzuführen, kann dies zu schwerwiegenden Problemen mit Adobe Commerce führen. Bitte beachten Sie, dass Service-Upgrades auf der Cloud-Infrastruktur von Adobe Commerce nicht in die Produktionsumgebung übertragen werden können, ohne dass unser Infrastrukturteam 48 Geschäftszeiten benachrichtigt. Dies ist erforderlich, da wir sicherstellen müssen, dass wir über einen Infrastruktur-Support-Mitarbeiter verfügen, der Ihre Konfiguration innerhalb eines gewünschten Zeitraums mit minimalen Ausfallzeiten in Ihrer Produktionsumgebung aktualisiert. 48 Stunden vor dem Zeitpunkt, zu dem Ihre Änderungen in der Produktion sein müssen [senden Sie ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), in dem Sie Ihre erforderliche Service-Aktualisierung und den Zeitpunkt angeben, zu dem der Upgrade-Prozess beginnen soll.

Der Grund für die Entfernung der MySQL-Suchmaschine liegt darin, dass Elasticsearch hervorragende Suchfunktionen sowie Katalogleistungsoptimierungen bietet.

## Betroffene Produkte und Versionen:

* Adobe Commerce On-Premise v2.4.0
* Magento Open Source v2.4.0

## Upgrade:

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
<td class="wysiwyg-text-align-center" style="width: 133px;">Elasticsearch (ohne aufgeführte Version)</td>
<td style="width: 478.2px;">Sie verwenden Elasticsearch 2 und müssen auf Elasticsearch 7 (empfohlen) oder 6 aktualisieren. Weitere Informationen finden Sie unter <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search#es-upgrade6">Aktualisieren von Elasticsearch</a> und <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/configure-search-engine">Konfigurieren von Commerce für die Verwendung von Elasticsearch</a> in unserer Entwicklerdokumentation.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">ELASTICSEARCH 5</td>
<td style="width: 478.2px;">Elasticsearch 5 hat das <a href="https://www.elastic.co/support/eol">Ende der Lebensdauer</a> erreicht und wird in Adobe Commerce 2.4.0 nicht mehr unterstützt. Aktualisierung auf Elasticsearch 7 (empfohlen) oder 6.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Elasticsearch 6 oder 7</td>
<td style="width: 478.2px;">Sie müssen keine weiteren Schritte ausführen, bevor Sie auf Adobe Commerce 2.4.0 aktualisieren.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Drittanbietererweiterung</td>
<td style="width: 478.2px;">Sie müssen Elasticsearch nicht installieren. Adobe Commerce empfiehlt Ihnen, sich an Ihren Suchmaschinenanbieter zu wenden, um festzustellen, ob Ihre Erweiterung vollständig mit Adobe Commerce 2.4.0 kompatibel ist.</td>
</tr>
</tbody>
</table>

## Installation:

Wenn Adobe Commerce lokal und Magento Open Source 2.4.0 veröffentlicht wird, ist Elasticsearch eine erforderliche Komponente. Daher müssen Sie vor der Installation von Version 2.4.0 über ein Elasticsearch-Host-Setup und eine Konfiguration verfügen. Siehe [Installieren und Konfigurieren von Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search) in unserer Entwicklerdokumentation.

Standardmäßig verwendet die Adobe Commerce-Suche Elasticsearch 7 als Suchmaschine und versucht, eine Verbindung zu einem Server unter localhost:9200 herzustellen. Elasticsearch 6.x wird ebenfalls unterstützt. Wenn Ihre Konfiguration nicht den Standardeinstellungen entspricht, können Sie diese Einstellungen mit den an `setup:install` übergebenen Argumenten konfigurieren, ähnlich wie die Datenbankverbindung konfiguriert ist.

Beispiel: `setup:install --elasticsearch-host=es.mystore.com`

Während der Installation wird die Elasticsearch-Verbindung überprüft und die Installation schlägt fehl, wenn Adobe Commerce keine Verbindung zu einem Elasticsearch-Host herstellen kann. In diesem Fall überprüfen Sie, ob Ihr Elasticsearch betriebsbereit ist und ob Sie die richtigen Verbindungsparameter angegeben haben.
