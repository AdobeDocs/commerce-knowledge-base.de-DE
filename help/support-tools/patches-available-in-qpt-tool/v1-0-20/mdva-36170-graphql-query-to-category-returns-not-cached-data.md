---
title: "MDVA-36170: GraphQL-Abfrage zur Kategorie gibt keine zwischengespeicherten Daten zurück"
description: Der Patch MDVA-36170 behebt das Problem, dass das Ergebnis der GraphQL-Abfrage nicht zwischengespeichert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 installiert ist. Die Patch-ID lautet MDVA-36170. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.
exl-id: 6249b751-4b71-4833-ab86-ded615d648a8
feature: Cache, GraphQL, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# MDVA-36170: GraphQL-Abfrage an Kategorie gibt nicht zwischengespeicherte Daten zurück

Der Patch MDVA-36170 behebt das Problem, dass das Ergebnis der GraphQL-Abfrage nicht zwischengespeichert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 installiert ist. Die Patch-ID lautet MDVA-36170. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce in Cloud-Infrastruktur 2.3.6

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.1 - 2.4.1-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Behebung des Problems, bei dem das Ergebnis der GraphQL-Abfrage nicht zwischengespeichert wurde.

<u>Zu reproduzierende Schritte</u>:

Der Händler verwendet die GET-Methode für die GraphQL-Zwischenspeicherung, ruft jedoch die zwischengespeicherten Daten nicht ab.

<pre>https://magento_url/graphql?query={ products(filter: {category_id: {eq: "2"}, pageSize: 2000, currentPage: 1, sort: {position: ASC}) {
items {
  sku
  id
  name
  description {
    html
  }
  url_key
  Spezifikationen
  image {
    label
    gallery_url
  }
  __typename
  quantity_in
  small_image {
    gallery_url
    label
  }
  product_price_range {
    maximum_price {
      final_price {
        value
      }
    }
    minimum_price {
      final_price {
        value
      }
    }
  }
  ... auf ConfigurableProduct {
    Varianten{
      attributes{
        code
        label
        value_index
      }
      product{
        sku
        quantity_in
      }
    }
   }
  }
}
}}</pre>

<u>Erwartete Ergebnisse</u>:

Die Daten werden zwischengespeichert.

<u>Tatsächliche Ergebnisse</u>:

Die Daten werden nicht zwischengespeichert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
