---
title: Kundengruppennamen, Segmente und Informationen zu Werberegeln, die über verfügbar gemacht werden [!DNL GraphQL]
description: Dieser Artikel enthält einen Hotfix, um die Offenlegung von Kundengruppennamen, Kundensegmenten und Informationen zu Werberegeln über  [!DNL GraphQL] zu verhindern.
feature: GraphQL
role: Admin, Developer
source-git-commit: f32085c80c9dbce513dad15ebf5f77a0e6398466
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---


# Namen von Kundengruppen, Segmente und Informationen zu Werberegeln, die über [!DNL GraphQL] bereitgestellt werden

Dieser Artikel enthält einen Hotfix, um die Offenlegung von Kundengruppennamen, Kundensegmenten und Informationen zu Werberichtlinien über [!DNL GraphQL] zu verhindern. Das Problem wird voraussichtlich in Adobe Commerce 2.4.8-p1 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.8

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.8

## Problem

[!UICONTROL Storefront Personalization Drop-ins] wurden neue [!DNL GraphQL]-Mutationen eingeführt, um grundlegende Informationen wie Kundengruppennamen, Segmente, Warenkorb und Katalogregeln anzuzeigen. Dies kann jedoch sensible Daten wie Angebotsdetails oder Coupon-Codes verfügbar machen, wenn sie in den Namen enthalten sind.

### Schritte zur Reproduktion

#### Fall I: [!UICONTROL Catalog Rule]

1. Navigieren Sie in *Admin*-Seitenleiste zu **[!UICONTROL Marketing]** > **[!UICONTROL Catalog Price Rule]** > **[!UICONTROL Add New Rule]**.
1. Definieren Sie die Regelbedingungen (z. B. Produktattribut oder Kategorie).
1. Speichern und wenden Sie die Regel an.
1. Stellen Sie sicher, dass ein Produkt die Regelbedingungen erfüllt.
1. Führen Sie die folgende [!DNL GraphQL] aus, um alle Regeln abzurufen:

   ```
   query {
       allCatalogRules {
           name
       }
   }
   ```

1. Fragen Sie ein Produkt ab, um zu überprüfen, ob die Regel anwendbar ist:

   ```
   query {
       products(filter: { sku: { eq: "product-sku" } }) {
           items {
               name
               rules {
                   name
               }
           }
       }
   }
   ```

#### Fall II: [!UICONTROL Cart Rule]

1. Navigieren Sie in *Admin*-Seitenleiste zu **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rule]** > **[!UICONTROL Add New Rule]**.
1. Legen Sie Bedingungen wie den minimalen Warenkorbwert und die Kundengruppe fest.
1. Speichern und wenden Sie die Regel an.
1. Fügen Sie Produkte zum Warenkorb hinzu, um die Regel zum Trigger hinzuzufügen.
1. Verwenden Sie [!DNL GraphQL], um alle Regeln des Warenkorbs zu überprüfen:

   ```
   query {
       allCartRules {
           name
       }
   }
   ```

1. Überprüfen Sie, ob Regeln auf den aktiven Warenkorb angewendet werden:

   ```
   query {
       cart(cart_id: "your-cart-id") {
           rules {
               name
           }
       }
   }
   ```

#### Fall III: [!UICONTROL Customer Group]

1. Navigieren Sie in der *Admin*-Seitenleiste zu **[!UICONTROL Customers]** > **[!UICONTROL Customer Groups]**.
1. Überprüfen Sie, ob die erwarteten Gruppen vorhanden sind.
1. Verwenden Sie [!DNL GraphQL], um alle Gruppen abzurufen:

   ```
   query {
       allCustomerGroups {
           name
       }
   }
   ```

1. Überprüfen Sie die Gruppe des Kunden/Gastes:

   ```
   query {
       customerGroup {
           name
       }
   }
   ```

#### Fall IV: [!UICONTROL Customer Segment] (nur für Adobe Commerce)

1. Navigieren Sie in *Admin*-Seitenleiste zu **[!UICONTROL Customers]** > **[!UICONTROL Customer Segments]** → **[!UICONTROL Add Segment]**.
1. Definieren Sie kundenbasierte Bedingungen (z. B. Bestellung, Warenkorbinhalt).
1. Weisen Sie den entsprechenden Bereich zu: *[!UICONTROL Visitor]*, *[!UICONTROL Registered]* oder beides.
1. Stellen Sie sicher, dass die Bedingungen mit einem Testkunden übereinstimmen.
1. Verwenden Sie [!DNL GraphQL], um alle Segmente zu überprüfen:

   ```
   query {
       allCustomerSegments {
           name
           apply_to
       }
   }
   ```

1. Validieren der auf einen Warenkorb angewendeten Segmente:

   ```
   query {
       customerSegments(cartId: "your-cart-id") {
           name
       }
   }
   ```

<u>Erwartetes Ergebnis</u>:

Die Namen von Kundengruppen, Segmenten und Informationen zu Werberegeln werden nicht über [!DNL GraphQL] verfügbar gemacht.

<u>Tatsächliches </u>:

Die Namen von Kundengruppen, Segmenten und Informationen zu Werberegeln werden über [!DNL GraphQL] verfügbar gemacht.

## Lösung

Wenden Sie die angehängten Patches je nach Adobe Commerce-Version an:

* Für Adobe Commerce Version 2.4.8:

   * [LYNX-839_CE_2.4.8.patch](assets/LYNX-839_CE_2.4.8.patch.zip)
   * [LYNX-839_EE_2.4.8.patch](assets/LYNX-839_EE_2.4.8.patch.zip)

* Für [!DNL Magento] öffnen Sie Source Version 2.4.8:

   * [LYNX-839_CE_2.4.8.patch](assets/LYNX-839_CE_2.4.8.patch.zip)
