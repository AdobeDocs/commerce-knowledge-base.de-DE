---
title: MySQL und Elasticsearch zeigen unterschiedliche Ergebnisse an
description: Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce-Problem in der Cloud-Infrastruktur 2.2.3, das sich auf das Abrufen verschiedener Suchergebnisse für dieselbe Suchabfrage mit MySQL und Elasticsearch bezieht.
exl-id: 37a0164a-0237-4200-ab9c-e0dbad7e2062
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# MySQL und Elasticsearch zeigen unterschiedliche Ergebnisse an

>[!WARNING]
>
> [Die MySQL-Katalogsuchmaschine wird in Adobe Commerce 2.4.0 entfernt](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). Sie müssen den Elasticsearch-Host vor der Installation von Version 2.4.0 einrichten und konfigurieren lassen. Siehe Abschnitt [Installieren und Konfigurieren von Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html) in unserer Entwicklerdokumentation.

Dieser Artikel enthält einen Patch für das bekannte Adobe Commerce-Problem in der Cloud-Infrastruktur 2.2.3, das sich auf das Abrufen verschiedener Suchergebnisse für dieselbe Suchabfrage mit MySQL und Elasticsearch bezieht.

## Problem:

Ihre Katalogsuchergebnisse mit demselben Filtersatz unterscheiden sich je nach verwendeter Suchmaschine, MySQL oder Elasticsearch.

<u>Zu reproduzierende Schritte</u> :

1. Installieren und konfigurieren Sie Elasticsearch.
1. Wählen Sie in der Storefront einen der Filter aus.
1. Notieren Sie sich die Anzahl der übereinstimmenden Produkte.
1. Standardkonfiguration [MySQL-Suche](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md).
1. Wählen Sie in der Storefront einen der Filter aus.
1. Notieren Sie sich die Anzahl der übereinstimmenden Produkte.

<u>Erwartetes Ergebnis</u>: Die Anzahl der übereinstimmenden Produkte ist identisch.

<u>Tatsächliches Ergebnis</u>: Die Anzahl der übereinstimmenden Produkte ist unterschiedlich.

## Patch

Die Patches sind diesem Artikel beigefügt. Um einen Patch herunterzuladen, scrollen Sie nach unten zum Ende des Artikels und klicken Sie auf den erforderlichen Dateinamen oder auf die folgenden Links:

[MDVA-12312\_EE\_2.2.3\_COMPOSER\_v1.patch herunterladen](assets/MDVA-12312_EE_2.2.3_COMPOSER_v1.patch.zip)

[MDVA-14172\_EE\_2.2.6\_COMPOSER\_v1.patch herunterladen](assets/MDVA-14172_EE_2.2.6_COMPOSER_v1.patch.zip)

### Kompatible Adobe Commerce-Versionen:

Die Patches wurden für Folgendes erstellt:

* Adobe Commerce auf Cloud-Infrastruktur 2.2.3 (die `MDVA-12312_EE_2.2.3_COMPOSER_v1.patch` -Datei)
* Adobe Commerce in Cloud-Infrastruktur 2.2.6 (die `MDVA-14172_EE_2.2.6_COMPOSER_v1.patch` -Datei)

Die `MDVA-12312_EE_2.2.3_COMPOSER_v1.patch` Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):

* Adobe Commerce in Cloud-Infrastruktur 2.2.4
* Adobe Commerce in Cloud-Infrastruktur 2.2.5
* Adobe Commerce vor Ort 2.2.3
* Adobe Commerce vor Ort 2.2.4
* Adobe Commerce vor Ort 2.2.5

Die `MDVA-14172_EE_2.2.6_COMPOSER_v1.patch` Patch ist auch mit den folgenden Adobe Commerce-Versionen und -Editionen kompatibel (löst das Problem jedoch möglicherweise nicht):

* Adobe Commerce vor Ort 2.2.6

## Anwenden des Pflasters

Siehe [Anwenden eines von Adobe bereitgestellten Composer-Patches](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in unserer Support-Wissensdatenbank für Anleitungen.

## Attached Files
