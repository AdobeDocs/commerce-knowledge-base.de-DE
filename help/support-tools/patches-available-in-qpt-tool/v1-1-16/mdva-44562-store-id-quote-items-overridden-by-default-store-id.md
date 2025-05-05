---
title: 'MDVA-44562: Store-ID für Angebotselemente, die durch die standardmäßige Store-ID überschrieben werden'
description: Der Patch MDVA-44562 behebt das Problem, dass die standardmäßige Store-ID die Store-ID für Angebotselemente für GraphQL-Anfragen überschreibt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 installiert ist. Die Patch-ID lautet MDVA-44562. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.
exl-id: 902bfc05-411d-4a6c-a6e8-cd7376629b0c
feature: Quotes
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# MDVA-44562: Store-ID für Angebotselemente, die durch die standardmäßige Store-ID überschrieben werden

Der Patch MDVA-44562 behebt das Problem, dass die standardmäßige Store-ID die Store-ID für Angebotselemente für GraphQL-Anfragen überschreibt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 installiert ist. Die Patch-ID lautet MDVA-44562. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Store-ID für Angebotselemente wird durch die standardmäßige Store-ID für GraphQL-Anfragen überschrieben.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine neue Store-Ansicht.
1. Erstellen Sie ein neues einfaches Produkt mit unterschiedlichen Namen pro Shop-Ansicht.
1. Neuen Kunden erstellen.
1. Abrufen des Kunden-Autorisierungs-Tokens.

   ```GraphQL
    POST /rest/all/V1/integration/customer/token
    {
      "username": "test@example.com",
      "password": "password"
     }
   ```

1. Erstellen Sie mithilfe des Autorisierungs-Tokens ein neues Angebot für den Kunden.

   ```GraphQL
   POST rest/default/V1/carts/mine
   ```

1. Fügen Sie ein Produkt zum Warenkorb hinzu.

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

1. Rufen Sie den Inhalt des Warenkorbs für die standardmäßige Store-Ansicht ab.

   ```GraphQL
   GET rest/default/V1/carts/mine/
   ```

1. Rufen Sie den Inhalt des Warenkorbs für die neue Store-Ansicht ab.

   ```GraphQL
   GET rest/<store_view_2>/V1/carts/mine/
   ```

<u>Erwartete Ergebnisse</u>:

Die Antwort der neuen Store-Ansicht zeigt den Produktnamen der neuen Store-Ansicht an.

<u>Tatsächliche Ergebnisse</u>:

Die Antwort aus der neuen Store-Ansicht zeigt die Einrichtung des Produktnamens unter der Standard-Store-Ansicht an.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
