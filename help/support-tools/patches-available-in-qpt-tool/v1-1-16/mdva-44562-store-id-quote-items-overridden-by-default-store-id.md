---
title: "MDVA-44562: Store-ID für Anführungszeichen-Elemente, die durch die Standard-Store-ID überschrieben werden"
description: Der Patch MDVA-44562 behebt das Problem, dass die standardmäßige Store-ID die Store-ID für Anführungselemente für GraphQL-Anforderungen überschreibt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 installiert ist. Die Patch-ID lautet MDVA-44562. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.
exl-id: 902bfc05-411d-4a6c-a6e8-cd7376629b0c
feature: Quotes
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# MDVA-44562: Store-ID für Anführungselemente, die durch die standardmäßige Store-ID überschrieben werden

Der Patch MDVA-44562 behebt das Problem, dass die standardmäßige Store-ID die Store-ID für Anführungselemente für GraphQL-Anforderungen überschreibt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 installiert ist. Die Patch-ID lautet MDVA-44562. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Store-ID für Anführungselemente wird von der standardmäßigen Store-ID für GraphQL-Anforderungen überschrieben.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine neue Store-Ansicht.
1. Erstellen Sie ein neues einfaches Produkt mit unterschiedlichen Namen pro Store-Ansicht.
1. Erstellen Sie einen neuen Kunden.
1. Besorgen Sie sich das Token für die Kundenautorisierung.

   ```GraphQL
    POST /rest/all/V1/integration/customer/token
    {
      "username": "test@example.com",
      "password": "password"
     }
   ```

1. Erstellen Sie mit dem Autorisierungstoken ein neues Angebot für den Kunden.

   ```GraphQL
   POST rest/default/V1/carts/mine
   ```

1. Fügen Sie dem Warenkorb ein Produkt hinzu.

   ```GraphQL
   POST /rest/default/V1/carts/mine/items
   {
     "cartItem": {
       "sku": "simple1",
       "qty": 1,
       "quote_id": "1"
     }
   }
   ```

1. Rufen Sie den Warenkorbinhalt für die standardmäßige Store-Ansicht ab.

   ```GraphQL
   GET rest/default/V1/carts/mine/
   ```

1. Rufen Sie den Warenkorbinhalt für die neue Store-Ansicht ab.

   ```GraphQL
   GET rest/<store_view_2>/V1/carts/mine/
   ```

<u>Erwartete Ergebnisse</u>:

Die Antwort aus der neuen Store-Ansicht zeigt den Produktnamen aus der neuen Store-Ansicht an.

<u>Tatsächliche Ergebnisse</u>:

Die Antwort aus der neuen Store-Ansicht zeigt die Einrichtung des Produktnamen unter der standardmäßigen Store-Ansicht an.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) verfügbar sind, in unserer Entwicklerdokumentation.
