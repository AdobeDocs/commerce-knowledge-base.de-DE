---
title: 'MDVA-43102: Verkaufsmenge nicht korrekt aktualisiert'
description: Der Patch MDVA-43102 behebt das Problem, dass die Verkaufsmenge nicht korrekt aktualisiert wird, wenn eine Rückerstattung über die REST-API erfolgt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-43102. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: c51bc45b-a7e0-4581-a318-9c4736e6661c
feature: Variables
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-43102: Verkaufsmenge nicht korrekt aktualisiert

Der Patch MDVA-43102 behebt das Problem, dass die Verkaufsmenge nicht korrekt aktualisiert wird, wenn eine Rückerstattung über die REST-API erfolgt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-43102. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.1 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Verkaufsmenge wird nicht korrekt aktualisiert, wenn eine Rückerstattung mithilfe der REST-API erfolgt.

<u>Zu reproduzierende Schritte</u>:

1. Fügen Sie dem Warenkorb einen Artikel hinzu.
1. Überprüfen Sie die Lagermenge und die Verkaufsmenge.
1. Erstellen Sie eine Bestellung.
1. Erstellen Sie bei Bedarf eine Rechnung.
1. Senden Sie eine REST-Anfrage zur Rückerstattung der Rechnung mit der folgenden Payload:

   * Offline-Methode/Bestellung/`<order_id>`/Rückgabe
   * Online-Methode/Rechnung/`<invoice_id>`/Erstattung

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

1. Versenden Sie die Artikel nicht.
1. Vergleichen Sie die Lagermenge und die Salable Qty von vorher. Beide sollten um denselben Betrag aktualisiert werden.

<u>Erwartete Ergebnisse</u>:

Die Verkaufsmenge wird korrekt aktualisiert, wenn eine Rückerstattung vor dem Versand der Bestellung erteilt wird und das Produkt wieder auf den Lager zurückgegeben wird.

<u>Tatsächliche Ergebnisse</u>:

Die Verkaufsmenge wird nicht aktualisiert, wenn eine Rückerstattung vor dem Versand der Bestellung erteilt wird, und das Produkt wird an den Lager zurückgegeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) verfügbar sind, in unserer Entwicklerdokumentation.
