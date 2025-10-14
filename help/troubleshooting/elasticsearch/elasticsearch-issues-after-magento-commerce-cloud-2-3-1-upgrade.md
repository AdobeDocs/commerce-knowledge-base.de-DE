---
title: Elasticsearch-Probleme nach der Aktualisierung auf Adobe Commerce Cloud Infrastructure 2.3.1+
description: In diesem Artikel wird eine Fehlerbehebung für Probleme während der Bereitstellung nach dem Upgrade auf Adobe Commerce unter Cloud-Infrastrukturversionen 2.3.1 oder höher beschrieben, wenn Sie Elasticsearch-Versionen 2.x und 5.x verwenden.
exl-id: 6ceeb2ea-528d-4c03-ab2b-c5aed46fd0a2
feature: Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# Elasticsearch-Probleme nach der Aktualisierung auf Adobe Commerce Cloud Infrastructure 2.3.1+

>[!WARNING]
>
>[Die MySQL-Katalogsuchmaschine wird in Adobe Commerce 2.4.0 entfernt](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). Vor der Installation von Version 2.4.0 müssen Sie den Elasticsearch-Host eingerichtet und konfiguriert haben. Siehe [Installieren und Konfigurieren von Elasticsearch](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/search/overview-search).

>[!WARNING]
>
>Bitte beachten Sie, dass Service-Upgrades erst nach einer Vorankündigung von 48 Geschäftsstunden an unser Infrastruktur-Team in die Produktionsumgebung übertragen werden können. Dies ist erforderlich, da wir sicherstellen müssen, dass wir einen Support-Techniker für die Infrastruktur zur Verfügung haben, der Ihre Konfiguration innerhalb eines gewünschten Zeitraums mit minimalen Ausfallzeiten in Ihrer Produktionsumgebung aktualisiert. 48 Stunden vor dem Zeitpunkt, zu dem Ihre Änderungen in der Produktion vorgenommen werden müssen ([&#x200B; ein Support-Ticket &#x200B;](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)), wobei das erforderliche Service-Upgrade detailliert angegeben und der Zeitpunkt angegeben wird, zu dem das Upgrade gestartet werden soll.

In diesem Artikel wird eine Fehlerbehebung für Probleme während der Bereitstellung nach dem Upgrade auf Adobe Commerce unter Cloud-Infrastrukturversionen 2.3.1 oder höher beschrieben, wenn Sie Elasticsearch-Versionen 2.x und 5.x verwenden.

## Betroffene Produkte und Versionen:

* Adobe Commerce auf Cloud-Infrastruktur 2.3.1+
* Elasticsearch 2.x und 5.x

## Ursache

Händler, die auf Adobe Commerce in der Cloud-Infrastruktur (Version 2.3.1 und höher) aktualisiert haben und eine Version von Elasticsearch vor 6.x verwenden, können bei der Bereitstellung Fehler auftreten. Dies liegt daran, dass die Elasticsearch-Versionen 2.x und 5[x auslaufen &#x200B;](https://www.elastic.co/support/eol) und in Adobe Commerce nicht mehr unterstützt werden. Der Elasticsearch-Client muss auf dem neuesten Stand sein, da andernfalls beim Ausführen einer Bereitstellung ein Fehler ausgelöst werden könnte. Weitere Informationen finden Sie unter [Ändern des Elasticsearch-Clients](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/search/overview-search) in unserer Entwicklerdokumentation.

## Problem

Bei der Bereitstellung wird eine Fehlermeldung wie die folgende angezeigt, die darauf hinweist, dass Ihre Elasticsearch-Version nicht kompatibel ist: *Elasticsearch-Service-Version 5.2.2 auf der Infrastrukturschicht ist nicht kompatibel mit der aktuellen Version des Elasticsearch/Elasticsearch-Moduls (6.7.0.0), das von Ihrer Magento-Anwendung verwendet wird.* *Sie können dieses Problem beheben, indem Sie den Elasticsearch-Service auf Ihrer Magento-Cloud-Infrastruktur auf Version 6.x*. Andere Symptome dieses Problems können fehlende Bilder und Probleme mit Filtern in Ihrer Umgebung sein.

## Lösung

>[!WARNING]
>
>Wenn Sie über eine gemeinsam genutzte Umgebung verfügen, stellen Sie sicher, dass Staging und Produktion für ein Upgrade bereit sind.

Um dieses Problem zu beheben, müssen das Elasticsearch-Client-Modul und der Elasticsearch-Service die neuesten empfohlenen Versionen verwenden:

1. Befolgen Sie die Anweisungen [Ändern des Elasticsearch-Moduls](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/search/overview-search) in unserer Entwicklerdokumentation, damit Sie über die neueste empfohlene Version des Elasticsearch-Client-Moduls verfügen.
1. [Senden Sie ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) und fordern Sie ein Elasticsearch-Service-Update für Staging und Produktion auf 6.x an. Bitte beachten Sie, dass es einige Zeit dauern kann, bis eine Aktualisierung des Elasticsearch-Service abgeschlossen ist.

## Verwandtes Lesen

* [Anforderungen für den Technologie-Stack von Adobe Commerce 2.3](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/overview) in unserer Entwicklerdokumentation.
* [Einrichten des Elasticsearch-](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch) in unserer Entwicklerdokumentation.
* [Installieren und Konfigurieren von Elasticsearch](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/search/overview-search) finden Sie in unserer Entwicklerdokumentation.
* [Stellen Sie sicher, dass das Elasticsearch ordnungsgemäß installiert &#x200B;](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md), in unserer Support-Wissensdatenbank.
