---
title: 'ACSD-50794: Geschenkverpackung kann nicht von der Kundenbestellung über GraphQL entfernt werden'
description: Wenden Sie den Patch ACSD-50794 an, um das Adobe Commerce-Problem zu beheben, bei dem Benutzende Geschenkverpackungen nicht über GraphQL aus der Kundenbestellung entfernen können.
exl-id: 4983910c-9ea0-451e-a2b6-81485184bbce
feature: Gift, GraphQL, Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-50794: Geschenkverpackung kann nicht von der Kundenbestellung über GraphQL entfernt werden

Mit dem Patch ACSD-50794 wird das Problem behoben, dass Benutzende Geschenkverpackungen nicht über GraphQL aus der Kundenbestellung entfernen können. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32 installiert ist. Die Patch-ID ist ACSD-50794. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Benutzende können Geschenkverpackungen nicht über GraphQL aus der Kundenbestellung entfernen.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie einen Kunden aus dem Frontend.
1. Erstellen Sie ein einfaches Produkt.
1. Aktivieren Sie *[!UICONTROL Gift Messages]*, indem Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Options]** wechseln und *[!UICONTROL Allow Gift Messages]* = *[!UICONTROL Yes]* festlegen.
1. Erstellen Sie *[!UICONTROL Gift Wrapping]* über **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Gift Wrapping]**.
1. Kunden-Token abrufen.
1. Erstellen Sie einen leeren Warenkorb, customerCart.
   * Fügen Sie Produkte zum Warenkorb hinzu: `addProductsToCart` Mutation
   * Rechnungsadresse festlegen: `setBillingAddressOnCart` Mutation
   * Lieferadresse festlegen: `setShippingAddressesOnCart` Mutation
   * Versandmethode festlegen: `setShippingMethodsOnCart` Mutation (Flatrate)
   * Zahlungsmethode festlegen: `setPaymentMethodOnCart` Mutation (checkmo)
1. Überprüfen Sie nun mit dieser Warenkorbabfrage *Geschenkverpackung* UID):

   <pre><code class="language-GraphQL">
    &lbrace;
      cart(cart_id: "{{CART_ID}}") &lbrace;
        available_gift_wrappings&lbrace;
            uid
        &rbrace;
    &rbrace;
    &rbrace;
    </code></pre>

1. Geschenkverpackung mit `setGiftOptionsOnCart` festlegen.
1. Überprüfen Sie den Warenkorb: Warenkorbabfrage.
1. Geschenkverpackung mit `setGiftOptionsOnCart` aufheben (Wert auf null setzen).
1. Überprüfen Sie erneut den Warenkorb: Warenkorbabfrage.
1. Place order: `placeOrder` Mutation.
1. Führen Sie die Kundenabfrage aus: customer.

   <pre><code class="language-graphql">
    query &lbrace;
      customer &lbrace;
        firstname
        middlename
        lastname
        suffix
        email
        orders &lbrace;
            items &lbrace;
                order_date
                gift_wrapping &lbrace;
                    design
                    uid
                &rbrace;
            &rbrace;
        &rbrace;
        addresses &lbrace;
          firstname
          middlename
          lastname
          street
          city
          region &lbrace;
            region_code
            region
          &rbrace;
          postcode
          country_code
          telephone
        &rbrace;
      &rbrace;
    &rbrace;
    </code></pre>

<u>Erwartete Ergebnisse</u>:

Sobald ein Benutzer einen Geschenkumbruch einstellt und aufhebt, gibt die Kundenabfrage null zurück.

<u>Tatsächliche Ergebnisse</u>:

Die Kundenabfrage gibt weiterhin den angewendeten Geschenkumbruch zurück.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
