---
title: "ACSD-50260: GraphQL-Produktsuchergebnisse sind begrenzt"
description: Wenden Sie den Patch ACSD-50260 an, um das Adobe Commerce-Problem zu beheben, bei dem die GraphQL-Produktsuchergebnisse nur auf 10.000 Ergebnisse beschränkt sind.
exl-id: 89234a72-a633-4f57-923c-cb5bbcea0fd0
feature: Admin Workspace, Categories, GraphQL, Products, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# ACSD-50260: GraphQL-Produktsuchergebnisse sind begrenzt

Der Patch ACSD-50260 behebt das Problem, dass die GraphQL-Produktsuchergebnisse nur auf 10.000 Ergebnisse beschränkt sind. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 ist installiert. Die Patch-ID ist ACSD-50260. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.5-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die GraphQL-Produktsuchergebnisse sind auf 10.000 Ergebnisse beschränkt.

<u>Zu reproduzierende Schritte</u>:

1. Erzeugen *[!UICONTROL 15,000 products]* in einer Kategorie.
1. Abfragen dieser Kategorie mit der unten angehängten GraphQL-Anfrage:

```GraphQL
{
  products(
    filter: { category_id: { eq: "{CATEGORY_ID}" } }
    pageSize: 5
    currentPage: 1
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

`total_count = 15k`

Möglichkeit, alle Produkte in den Suchergebnissen zu erhalten.

<u>Tatsächliche Ergebnisse</u>:

`total_count = 10k`

Es besteht keine Möglichkeit, Produkte nach diesem 10.000-Batch in den Suchergebnissen zu erhalten.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
