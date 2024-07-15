---
title: "MDVA-35356: Falsche Store-Kreditwiedergabe nach Stornierung teilweise fakturierter Bestellungen"
description: Der Patch MDVA-35356 behebt das Problem mit einer falschen Rückgabe von Store-Krediten nach teilweise fakturierter Auftragsstornierung. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 installiert ist. Die Patch-ID lautet MDVA-35356. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben wurde.
exl-id: af37f318-0818-4393-b768-939f08b73847
feature: Invoices, Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# MDVA-35356: Falsche Stornobestätigung nach Stornierung teilweise in Rechnung gestellter Bestellungen

Der Patch MDVA-35356 behebt das Problem mit einer falschen Rückgabe von Store-Krediten nach teilweise fakturierter Auftragsstornierung. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 installiert ist. Die Patch-ID lautet MDVA-35356. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce in Cloud-Infrastruktur 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0-2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie drei einfache Produkte.
1. Erstellen Sie einen neuen Benutzer und weisen Sie Speichergutschriften zu (Beispiel: Store Credit = *$10,* einfache Produktpreise = *$100*, *$200* und *$300*).
1. Melden Sie sich mit dem obigen Benutzer an und fügen Sie die drei Produkte zum Warenkorb hinzu.
1. Sehen Sie sich die drei Produkte im Warenkorb an und verwenden Sie die Gutschrift für einen Teil der Bestellung (Beispiel: Bezahlt mit **Scheck-/Money-Bestellung**).
1. Führen Sie zwei Rechnungen für die Bestellung über die API aus, eine für Produkt 1 und eine für Produkt 2:

   ```php
   //endpoint POST {\{baseUrl}}/V1/order/:orderId/invoice    //1st API call:    {    "capture": true,    "items": [    {    "order_item_id": 1,    "qty": 1    }    ],    "notify": true,    "appendComment": false    }    //2nd API call:    {    "capture": true,    "items": [    {    "order_item_id": 2,    "qty": 1    }    ],    "notify": true,    "appendComment": false    }
   ```

1. Beachten Sie, dass das Store-Guthaben vollständig auf die erste Rechnung angewendet wird.
1. &#x200B; beachten Sie, dass der Store-Guthaben = *0* ist.
1. Abbrechen Sie die Bestellung und sehen Sie, dass zwei Elemente in Rechnung gestellt und das dritte Element abgebrochen wird.
1. Beobachten Sie das Kreditkonto des Stores.

<u>Erwartete Ergebnisse</u>:

Das Konto für das Geschäft ist immer noch 0, da das 10-Dollar-Geschäft-Guthaben in Rechnung gestellt wurde.

<u>Tatsächliche Ergebnisse</u>:

Der volle Store-Guthaben wird zurückgegeben: der Saldo beträgt 10 USD.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
