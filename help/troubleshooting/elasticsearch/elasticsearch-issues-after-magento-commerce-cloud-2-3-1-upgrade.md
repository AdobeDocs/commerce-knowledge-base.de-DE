---
title: Elasticsearch-Probleme nach der Aktualisierung der Adobe Commerce-Cloud-Infrastruktur 2.3.1+
description: In diesem Artikel wird eine Fehlerbehebung für Probleme während der Bereitstellung nach der Aktualisierung auf Adobe Commerce auf Cloud-Infrastrukturversionen 2.3.1+ beschrieben, wenn Sie Elasticsearch-Versionen 2.x und 5.x verwenden.
exl-id: 6ceeb2ea-528d-4c03-ab2b-c5aed46fd0a2
feature: Cloud
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# Elasticsearch-Probleme nach der Aktualisierung der Adobe Commerce-Cloud-Infrastruktur 2.3.1+

>[!WARNING]
>
>[Die MySQL-Katalogsuchmaschine wird in Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md) entfernt. Sie müssen den Elasticsearch-Host vor der Installation von Version 2.4.0 eingerichtet und konfiguriert haben. Siehe [Elasticsearch installieren und konfigurieren](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html).

>[!WARNING]
>
>Bitte beachten Sie, dass Service-Upgrades nicht ohne 48-Stunden-Benachrichtigung an unser Infrastrukturteam in die Produktionsumgebung gesendet werden können. Dies ist erforderlich, da wir sicherstellen müssen, dass wir über einen Infrastruktur-Support-Mitarbeiter verfügen, der Ihre Konfiguration innerhalb eines gewünschten Zeitraums mit minimalen Ausfallzeiten in Ihrer Produktionsumgebung aktualisiert. 48 Stunden vor dem Zeitpunkt, zu dem Ihre Änderungen in der Produktion sein müssen [senden Sie ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), in dem Sie Ihre erforderliche Service-Aktualisierung und den Zeitpunkt angeben, zu dem der Upgrade-Prozess beginnen soll.

In diesem Artikel wird eine Fehlerbehebung für Probleme während der Bereitstellung nach der Aktualisierung auf Adobe Commerce auf Cloud-Infrastrukturversionen 2.3.1+ beschrieben, wenn Sie Elasticsearch-Versionen 2.x und 5.x verwenden.

## Betroffene Produkte und Versionen:

* Adobe Commerce in Cloud-Infrastruktur 2.3.1+
* Elasticsearch 2.x und 5.x

## Ursache

Bei Merchants, die auf Adobe Commerce in der Cloud-Infrastruktur (ab Version 2.3.1) aktualisiert haben und eine Elasticsearch-Version vor 6.x verwenden, können bei der Bereitstellung Fehler auftreten. Dies liegt daran, dass die Elasticsearch-Versionen 2.x und 5.x [Ende der Lebensdauer](https://www.elastic.co/support/eol) sind und in Adobe Commerce nicht mehr unterstützt werden. Der Elasticsearch-Client muss auf dem neuesten Stand sein oder die Ausführung einer Bereitstellung birgt das Risiko, einen Fehler auszulösen. Weitere Informationen finden Sie unter [Ändern des Elasticsearch-Clients](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-downgrade.html) in unserer Entwicklerdokumentation.

## Problem

Bei der Bereitstellung wird eine Fehlermeldung ähnlich der folgenden angezeigt, die angibt, dass Ihre Elasticsearch-Version nicht kompatibel ist: *Elasticsearch-Dienst Version 5.2.2 auf Infrastrukturebene ist nicht mit der aktuellen Version des von Ihrer Magento-Anwendung verwendeten Elasticsearch-/Elasticsearch-Moduls (6.7.0.0) kompatibel.* *Sie können dieses Problem beheben, indem Sie den Elasticsearch-Dienst in Ihrer Magento Cloud-Infrastruktur auf Version 6.x* aktualisieren. Weitere Symptome dieses Problems sind möglicherweise fehlende Bilder und Probleme mit Filtern in Ihrer Umgebung.

## Lösung

>[!WARNING]
>
>Wenn Sie über eine freigegebene Umgebung verfügen, stellen Sie sicher, dass Staging und Produktion für die Aktualisierung bereit sind.

Um dieses Problem zu beheben, müssen das Elasticsearch-Client-Modul und der Elasticsearch-Dienst auf den neuesten empfohlenen Versionen basieren:

1. Befolgen Sie die Anweisungen unter [Ändern des Elasticsearch-Moduls](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-downgrade.html) in unserer Entwicklerdokumentation, sodass Sie über die neueste empfohlene Version des Elasticsearch-Client-Moduls verfügen.
1. [Senden Sie ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) und fordern Sie ein Elasticsearch-Service-Update auf 6.x für Staging und Produktion an. Bitte beachten Sie, dass ein Upgrade auf den Elasticsearch-Dienst einige Zeit in Anspruch nehmen kann.

## Verwandtes Lesen

* [Anforderungen an den Technologiestapel für Adobe Commerce 2.3](https://devdocs.magento.com/guides/v2.3/install-gde/system-requirements-tech.html) in unserer Entwicklerdokumentation.
* [Richten Sie den Elasticsearch-Dienst](https://devdocs.magento.com/cloud/project/project-conf-files_services-elastic.html) in unserer Entwicklerdokumentation ein.
* [Installieren und konfigurieren Sie Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html) in unserer Entwicklerdokumentation.
* [Stellen Sie sicher, dass Elasticsearch ordnungsgemäß installiert ist](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) in unserer Support-Wissensdatenbank.
