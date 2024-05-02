---
title: "ACSD-55610: Teilweise stornierte Bestellung hat falschen Rabattbetrag"
description: Wenden Sie den Patch ACSD-55610 an, um das Adobe Commerce-Problem zu beheben, bei dem eine teilweise stornierte Bestellung einen falschen Rabattbetrag aufweist.
feature: Invoices, Orders, Price Rules, Shopping Cart
role: Admin, Developer
exl-id: f4cca4fa-dc04-4c86-9176-c648b1d0e732
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-55610: Teilweise stornierte Bestellung hat falschen Rabattbetrag

Der Patch ACSD-55610 behebt das Problem, dass eine teilweise stornierte Bestellung einen falschen Rabattbetrag aufweist. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.43 ist installiert. Die Patch-ID ist ACSD-55610. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Eine teilweise stornierte Bestellung hat einen falschen Rabattbetrag.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine Preisregel für den Warenkorb.

   * *[!UICONTROL Rule Name]*: *Winterschlussverkauf*
   * *[!UICONTROL Active]* = *Ja*
   * *[!UICONTROL Websites]* = *Hauptwebsite*
   * Wählen Sie alle Kundengruppen aus.
   * Wählen Sie einen bestimmten Gutschein aus.
   * *[!UICONTROL Coupon Code]*: *WINTER10*
   * *[!UICONTROL Conditions]*: *[!UICONTROL If ALL of these conditions are TRUE]*: *Subtotal(Excl. Steuern) gleich oder größer als 75*
   * Anwenden *[!UICONTROL Percent of product price discount]*.
   * *[!UICONTROL Discount Amount]*: *10*
   * *[!UICONTROL Discard subsequent rules]*: *Ja*

1. Erstellen Sie drei Produkte mit Preisen von 100.
1. Fügen Sie die drei Produkte zum Warenkorb hinzu.
1. Wenden Sie den Gutschein an.
1. Platzieren Sie die Bestellung.
1. Invotieren Sie einen Artikel der Bestellung und schicken Sie ihn.
1. Abbrechen der beiden anderen Elemente.
1. Überprüfen Sie die `base_discount_canceled` Spalte.

<u>Erwartete Ergebnisse</u>:

Der Rabattbetrag in `base_discount_cancelled` korrekt widerspiegelt.

<u>Tatsächliche Ergebnisse</u>:

Die `base_discount_cancelled` nicht korrekt ist.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
