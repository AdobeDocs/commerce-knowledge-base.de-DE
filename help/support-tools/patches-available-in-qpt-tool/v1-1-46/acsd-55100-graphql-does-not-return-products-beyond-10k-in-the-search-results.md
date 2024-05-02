---
title: "ACSD-55100: [!DNL GraphQL] gibt in den Suchergebnissen keine Produkte zurück, die über 10.000 hinausgehen."
description: Wenden Sie den Patch ACSD-55100 an, um das Adobe Commerce-Problem zu beheben, bei dem die GraphQL in den Suchergebnissen keine Produkte über *10 k* zurückgibt.
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: 951e5cd4-9690-43df-9e51-deab73f9eb54
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# ACSD-55100: [!DNL GraphQL] gibt in den Suchergebnissen keine Produkte über 10.000 zurück

Der Patch ACSD-55100 behebt das Problem, bei dem [!DNL GraphQL] gibt keine Produkte zurück, die *10 k* in den Suchergebnissen. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46 installiert ist. Die Patch-ID ist ACSD-55100. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

[!DNL GraphQL] gibt keine Produkte zurück, die *10 k* in den Suchergebnissen.

<u>Voraussetzungen</u>:

Im Falle von **[!DNL OpenSearch]**, stellen Sie sicher, dass Sie die neueste verfügbare Version verwenden.

Um das gemeldete Problem zu beheben, wird die Funktion Point in Time eingeführt, die nach **[!DNL OpenSearch]** 2.5.0 und erfordert Version 2.2 des `opensearch-project/opensearch-php` Paket.

Es besteht jedoch ein Konflikt mit der `magento/magento-cloud-metapackage`, was eine Abhängigkeit von der `opensearch-project/opensearch-php` -Paket, das kleiner als Version 2.0.1 sein sollte.


Diese Abhängigkeit verhindert die Aktualisierung der [opensearch-project/opensearch-php] auf die neueste Version 2.2.

Daher tritt der folgende Fehler auf und gibt für Produkte, die *10.000*.

`Namespace [createPointInTime] not found in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Client.php:135`

Die vorhandene Abhängigkeit erschwert das direkte Hinzufügen einer Version zum `composer.json` und aktualisieren Sie die `opensearch-project/opensearch-php` auf Version 2.2.

Um das Problem zu beheben, fügen Sie die folgende Zeile in Ihre `composer.json` Datei unter dem erforderlichen Block. Stellen Sie anschließend erneut bereit, um das problematische Paket auf die neueste Version zu aktualisieren.

`"opensearch-project/opensearch-php": "2.2.0 as 2.0.0",`

<u>Zu reproduzierende Schritte</u>:

1. Generieren Sie den Katalog mit *15 k* Produkte.
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

Total_count = *15 k*
Sie sollten in der Lage sein, alle Produkte anzuzeigen.

<u>Tatsächliche Ergebnisse</u>:

Total_count = *10 k*
Sie können keine weiteren Produkte anzeigen lassen, die nach dem *10 k* Batch.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
