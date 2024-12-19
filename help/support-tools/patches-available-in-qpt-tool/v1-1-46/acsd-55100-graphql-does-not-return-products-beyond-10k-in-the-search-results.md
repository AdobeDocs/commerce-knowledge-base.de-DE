---
title: 'ACSD-55100: [!DNL GraphQL]  gibt in den Suchergebnissen keine Produkte zurück, die länger als 10 KB sind'
description: Wenden Sie den Patch ACSD-55100 an, um das Adobe Commerce-Problem zu beheben, bei dem GraphQL in den Suchergebnissen keine Produkte zurückgibt, die über *10k* hinausgehen.
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: 951e5cd4-9690-43df-9e51-deab73f9eb54
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# ACSD-55100: [!DNL GraphQL] gibt in den Suchergebnissen keine Produkte zurück, die länger als 10.000 sind

Mit dem Patch ACSD-55100 wird das Problem behoben, dass [!DNL GraphQL] in den Suchergebnissen keine Produkte über *10k* zurückgibt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46 installiert ist. Die Patch-ID ist ACSD-55100. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

[!DNL GraphQL] gibt in den Suchergebnissen keine Produkte zurück *die über 10* hinausgehen.

<u>Voraussetzungen</u>:

Stellen Sie im **[!DNL OpenSearch]** sicher, dass Sie die neueste verfügbare Version verwenden.

Um das gemeldete Problem zu beheben, wird die Point-in-Time-Funktion eingeführt, die nach **[!DNL OpenSearch]** 2.5.0 verfügbar ist und Version 2.2 des `opensearch-project/opensearch-php`-Pakets erfordert.

Es besteht jedoch ein Konflikt mit der `magento/magento-cloud-metapackage`, die eine Abhängigkeit vom `opensearch-project/opensearch-php` angibt, die kleiner als Version 2.0.1 sein sollte.


Diese Abhängigkeit verhindert, dass das Paket [opensearch-project/opensearch-php] auf die neueste Version 2.2 aktualisiert wird.

Daher tritt der folgende Fehler auf und gibt für Produkte mit einem Wert von mehr als *10.000 null*.

`Namespace [createPointInTime] not found in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Client.php:135`

Die vorhandene Abhängigkeit macht es schwierig, der `composer.json`-Datei direkt eine Version hinzuzufügen und das `opensearch-project/opensearch-php`-Paket auf Version 2.2 zu aktualisieren.

Um das Problem zu beheben, fügen Sie die folgende Zeile in Ihre `composer.json`-Hauptdatei unter dem erforderlichen Block ein. Stellen Sie anschließend erneut bereit, um das problematische Paket auf die neueste Version zu aktualisieren.

`"opensearch-project/opensearch-php": "2.2.0 as 2.0.0",`

<u>Schritte zur Reproduktion</u>:

1. Generieren Sie den Katalog mit *15k*-Produkten.
1. Senden Sie die [!DNL GraphQL]:

```
    query {
    products(
    filter: {
    # category_id:{eq:""}
    }
    , pageSize: 5, currentPage: 1

    ) {
    total_count
    page_info {
    current_page
    page_size
    total_pages
     }

     aggregations {

    attribute_code
    count
    label
    options {
    label
    value

    }
    }

    items {
    uid
    sku
    is_for_clearance
    categories {
    name
    breadcrumbs {
    category_name
    category_uid
    }
    display_mode
    description
    }
    }
    }
    }
```

<u>Erwartete Ergebnisse</u>:

total_count = *15k*
Sie sollten alle Produkte anzeigen können.

<u>Tatsächliche Ergebnisse</u>:

total_count = *10k*
Es können keine weiteren Produkte mehr angezeigt werden, nachdem der *10k* Batch.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
