---
title: 'MDVA-43348: GraphQL-Anfrage für Geschenkkarte zeigt Fehler an'
description: Der Patch MDVA-43348 behebt das Problem, dass die GraphQL-Anfrage der Geschenkkarte einen Fehler anzeigt, wenn „gift_card_options“ „uid“ enthalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-43348. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
exl-id: a9c0e1da-6698-463a-a6a8-60522f029b53
feature: Gift, GraphQL
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# MDVA-43348: GraphQL-Anfrage für Geschenkkarte zeigt Fehler an

Der Patch MDVA-43348 behebt das Problem, dass die GraphQL-Anfrage der Geschenkkarte einen Fehler anzeigt, wenn `gift_card_options` „uid“ enthalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-43348. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die GraphQL-Anfrage für Geschenkkarten zeigt einen Fehler an, wenn die Option für Geschenkkarten „uid“ enthält.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein Geschenkkartenprodukt.
1. Neuindizierung durchführen.
1. Führen Sie einen GraphQL-Aufruf durch, bei dem der URL-Schlüssel „Geschenkkarte“ lautet:

<pre>
<code class="language-graphql">
query getProductOptionsForProductPage_bypassFastly($urlKey: String!) {
  products(filter: { url_key: { eq: $urlKey } }) {
    items {
      id
      url_key
      ... on GiftCardProduct {
        allow_open_amount
        open_amount_min
        open_amount_max
        giftcard_type
        is_redeemable
        lifetime
        allow_message
        message_max_length
        gift_card_options {
          uid
          title
          required
        }
      }
    }
  }
}
</code>
</pre>

<u>Erwartete Ergebnisse</u>:

Geschenkkartendaten werden auf Anfrage zurückgegeben.

<u>Tatsächliche Ergebnisse</u>:

Der folgende Fehler tritt bei der Anfrage für Geschenkkartendaten auf:

<pre>
<code class="language-graphql">
{
  "errors": [
    {
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": {
        "category": "internal"
      },
      "locations": [
        {
          "line": 16,
          "column": 1
        }
      ],
      "path": [
        "products",
        "items",
        0,
        "gift_card_options",
        0,
        "uid"
      ]
    },
    {
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": {
        "category": "internal"
      },
      "locations": [
        {
          "line": 16,
          "column": 1
        }
      ],
      "path": [
        "products",
        "items",
        0,
        "gift_card_options",
        1,
        "uid"
      ]
    },
    {
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": {
        "category": "internal"
      },
      "locations": [
        {
          "line": 16,
          "column": 1
        }
      ],
      "path": [
        "products",
        "items",
        0,
        "gift_card_options",
        2,
        "uid"
      ]
    },
    {
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": {
        "category": "internal"
      },
      "locations": [
        {
          "line": 16,
          "column": 1
        }
      ],
      "path": [
        "products",
        "items",
        0,
        "gift_card_options",
        3,
        "uid"
      ]
    },
    {
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": {
        "category": "internal"
      },
      "locations": [
        {
          "line": 16,
          "column": 1
        }
      ],
      "path": [
        "products",
        "items",
        0,
        "gift_card_options",
        4,
        "uid"
      ]
    }
  ],
  "data": {
    "products": {
      "items": [
        {
          "id": 2,
          "url_key": "gitf-card",
          "allow_open_amount": false,
          "open_amount_min": null,
          "open_amount_max": null,
          "giftcard_type": "VIRTUAL",
          "is_redeemable": true,
          "lifetime": 0,
          "allow_message": true,
          "message_max_length": 255,
          "gift_card_options": [
            null,
            null,
            null,
            null,
            null
          ]
        }
      ]
    }
  }
}
</code>
</pre>

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in unserer Entwicklerdokumentation.
