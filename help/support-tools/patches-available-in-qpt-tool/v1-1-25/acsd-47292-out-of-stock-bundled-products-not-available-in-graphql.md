---
title: "ACSD-47292: Nicht vorrätige gebündelte Produkte sind in der GraphQL-Antwort nicht verfügbar"
description: Wenden Sie den Patch ACSD-47292 an, um das Adobe Commerce-Problem zu beheben, bei dem die nicht vorrätigen gebündelten Produkte nicht in der GraphQL-Antwort verfügbar sind, selbst wenn "Nicht vorrätige Produkte anzeigen"auf "Ja"eingestellt ist.
exl-id: 377dc62f-d1cd-4292-b25d-53c498b772a9
feature: Admin Workspace, Categories, GraphQL, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# ACSD-47292: Nicht vorrätige gebündelte Produkte sind in der GraphQL-Antwort nicht verfügbar

Der Patch ACSD-47292 behebt das Problem, dass die nicht vorrätigen gebündelten Produkte in der GraphQL-Antwort nicht verfügbar sind, selbst wenn die [!UICONTROL Display Out-of-Stock Products] auf *[!UICONTROL Yes]*. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 ist installiert. Die Patch-ID ist ACSD-47292. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die nicht vorrätigen gebündelten Produkte sind in der GraphQL-Antwort selbst dann nicht verfügbar, wenn die [!UICONTROL Display Out-of-Stock Products] auf *[!UICONTROL Yes]*.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu Adobe Commerce Admin > **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** und legen Sie die [!UICONTROL Display Out-of-Stock Products] nach *[!UICONTROL Yes]*.
1. Erstellen Sie zwei einfache Produkte: s1 und s2.
1. Machen Sie s1 nicht vorrätig und nicht einzeln sichtbar und s2 ist vorrätig und nicht einzeln sichtbar, und weisen Sie sie einer Kategorie zu.
1. Erstellen Sie ein gebündeltes Produkt mit mindestens einem Optionsprodukt und weisen Sie dieser Option s1 und s2 zu (Eingabetyp &quot;RadioButton&quot;).
1. Speichern Sie das gebündelte Produkt und weisen Sie es einer Kategorie zu.
1. Gehen Sie zur Storefront und öffnen Sie dieses gebündelte Produkt. Sie sehen, dass die nicht vorrätige Option s1 grau, aber sichtbar ist.
1. Senden einer GraphQL-Anforderung:

```GraphQL
{
  categoryList(filters: { ids: { in: ["3"] } }) {
    id
    name
    products(pageSize: 8, sort: { position: ASC }) {
      total_count
      items {
        id
        sku
        name
        ... on BundleProduct {
          url_key
          items {
            title
            sku
            options {
              quantity
              position
              is_default
              product {
                id
                name
                sku
              }
            }
          }
        }
      }
    }
  }
}
```

<u>Erwartete Ergebnisse</u>:

Die Option &quot;s1 bundle&quot;wird in der GraphQL-Antwort aufgeführt, da [!UICONTROL Display Out-of-Stock Products] auf *[!UICONTROL Yes]* und ist in der Storefront sichtbar.

<u>Tatsächliche Ergebnisse</u>:

Die Option &quot;s1 Bundle&quot;wird in der GraphQL-Antwort nicht aufgeführt.

```GraphQL
"items": [
                                {
                                    "title": "oo1",
                                    "sku": "bundle2",
                                    "options": [
                                        {
                                            "quantity": 1,
                                            "position": 2,
                                            "is_default": false,
                                            "product": {
                                                "id": 2,
                                                "name": "s2",
                                                "sku": "s2"
                                            }
                                        }
                                    ]
                                }
                            ]
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
