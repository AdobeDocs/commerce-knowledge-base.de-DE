---
title: MySQL und Elasticsearch zeigen unterschiedliche Ergebnisse
description: Dieser Artikel enthält einen Patch für das bekannte Problem Adobe Commerce on Cloud Infrastructure 2.2.3 im Zusammenhang mit dem Abrufen unterschiedlicher Suchergebnisse für dieselbe Suchabfrage mit MySQL und Elasticsearch.
exl-id: 37a0164a-0237-4200-ab9c-e0dbad7e2062
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# MySQL und Elasticsearch zeigen unterschiedliche Ergebnisse

>[!WARNING]
>
> [Die MySQL-Katalogsuchmaschine wird in Adobe Commerce 2.4.0 entfernt](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). Vor der Installation von Version 2.4.0 muss der Elasticsearch-Host eingerichtet und konfiguriert sein. Siehe [Installieren und Konfigurieren von Elasticsearch](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/search/overview-search) in unserer Entwicklerdokumentation.

Dieser Artikel enthält einen Patch für das bekannte Problem Adobe Commerce on Cloud Infrastructure 2.2.3 im Zusammenhang mit dem Abrufen unterschiedlicher Suchergebnisse für dieselbe Suchabfrage mit MySQL und Elasticsearch.

## Problem:

Ihre Katalogsuchergebnisse mit demselben Filtersatz unterscheiden sich je nach verwendeter Suchmaschine, MySQL oder Elasticsearch.

<u>Schritte zur Reproduktion</u> :

1. Installieren und Konfigurieren von Elasticsearch.
1. Wählen Sie in der Storefront einen der Filter aus.
1. Notieren Sie sich die Anzahl der passenden Produkte.
1. Konfigurieren Sie die Standardkonfiguration [MySQL-Suche](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md).
1. Wählen Sie in der Storefront einen der Filter aus.
1. Notieren Sie sich die Anzahl der passenden Produkte.

<u>Erwartetes Ergebnis</u>:
Die Anzahl der passenden Produkte ist gleich.

<u>Tatsächliches </u>:
Die Anzahl der passenden Produkte ist unterschiedlich.

## Fleck

Die Patches sind diesem Artikel beigefügt. Um einen Patch herunterzuladen, scrollen Sie nach unten zum Ende des Artikels und klicken Sie auf den gewünschten Dateinamen oder klicken Sie auf die folgenden Links:

[MDVA-12312\_EE\_2.2.3\_COMPOSER\_v1.patch herunterladen](assets/MDVA-12312_EE_2.2.3_COMPOSER_v1.patch.zip)

[MDVA-14172\_EE\_2.2.6\_COMPOSER\_v1.patch herunterladen](assets/MDVA-14172_EE_2.2.6_COMPOSER_v1.patch.zip)

### Kompatible Adobe Commerce-Versionen:

Die Patches wurden erstellt für:

* Adobe Commerce auf Cloud-Infrastruktur 2.2.3 (die `MDVA-12312_EE_2.2.3_COMPOSER_v1.patch`)
* Adobe Commerce auf Cloud-Infrastruktur 2.2.6 (die `MDVA-14172_EE_2.2.6_COMPOSER_v1.patch`)

Der `MDVA-12312_EE_2.2.3_COMPOSER_v1.patch` Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (kann jedoch das Problem möglicherweise nicht lösen):

* Adobe Commerce auf Cloud-Infrastruktur 2.2.4
* Adobe Commerce auf Cloud-Infrastruktur 2.2.5
* Adobe Commerce On-Premises 2.2.3
* Adobe Commerce On-Premises 2.2.4
* Adobe Commerce On-Premises 2.2.5

Der `MDVA-14172_EE_2.2.6_COMPOSER_v1.patch` Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (kann jedoch das Problem möglicherweise nicht lösen):

* Adobe Commerce On-Premises 2.2.6

## Anbringen des Pflasters

Anleitungen finden [&#x200B; in unserer Support](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)Wissensdatenbank unter „So wenden Sie einen Composer-Patch an, der von Adobe bereitgestellt wird“.

## Angehängte Dateien
