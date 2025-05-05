---
title: 'MDVA-43102: Verkaufsmenge nicht korrekt aktualisiert'
description: Der MDVA-43102 Patch behebt das Problem, dass die verkaufbare Menge nicht korrekt aktualisiert wird, wenn eine Rückerstattung über die REST-API erfolgt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-43102. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
exl-id: c51bc45b-a7e0-4581-a318-9c4736e6661c
feature: Variables
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-43102: Verkaufsmenge nicht korrekt aktualisiert

Der MDVA-43102 Patch behebt das Problem, dass die verkaufbare Menge nicht korrekt aktualisiert wird, wenn eine Rückerstattung über die REST-API erfolgt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-43102. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.1 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die verkaufbare Menge wird nicht korrekt aktualisiert, wenn eine Rückerstattung mithilfe der REST-API erfolgt.

<u>Schritte zur Reproduktion</u>:

1. Fügen Sie dem Warenkorb einen Artikel hinzu.
1. Überprüfen Sie die Lagermenge und die verkaufbare Menge.
1. Erstellen Sie eine Bestellung.
1. Erstellen Sie bei Bedarf eine Rechnung.
1. Senden Sie eine REST-Anfrage, um die Rechnung mit der folgenden Payload zurückzuerstatten:

   * Offline-Methode/Bestellung/`<order_id>`/Rückerstattung
   * Online-Methode/Rechnung/`<invoice_id>`/Rückerstattung

   ```rest
   {
     "items": [
     {
       "order_item_id": <order_item_id>,
       "qty": 1
     }
     ],
     "notify": true,
     "arguments": {
       "shipping_amount": 5,
       "extension_attributes": {
         "return_to_stock_items": [
         <order_item_id>
         ]
       }
     }
   }
   ```

1. Die Artikel nicht versenden.
1. Vergleichen Sie die Lagermenge mit der Verkaufsmenge von zuvor. Sie sollten beide um denselben Betrag aktualisiert werden.

<u>Erwartete Ergebnisse</u>:

Die verkaufsfähige Menge wird korrekt aktualisiert, wenn eine Rückerstattung vor dem Versand der Bestellung ausgestellt wird und das Produkt an den Lagerbestand zurückgegeben wird.

<u>Tatsächliche Ergebnisse</u>:

Die Verkaufsmenge wird nicht aktualisiert, wenn eine Rückerstattung vor dem Versand der Bestellung ausgestellt wird und das Produkt an den Lagerbestand zurückgegeben wird.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
