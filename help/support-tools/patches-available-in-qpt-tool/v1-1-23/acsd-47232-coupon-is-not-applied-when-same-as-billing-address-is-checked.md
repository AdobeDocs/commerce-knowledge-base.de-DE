---
title: '"ACSD-47232: Coupon wird nicht angewendet, wenn [!UICONTROL Same as Billing Address] ist markiert'''
description: Wenden Sie den Patch ACSD-47232 an, um das Adobe Commerce-Problem zu beheben, bei dem Coupon bei [!UICONTROL Same as Billing Address] aktiviert ist.
exl-id: 29b95a0b-8792-4830-a1e5-ce977f8453ec
feature: Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-47232: Coupon wird nicht angewendet, wenn [!UICONTROL Same as Billing Address] aktiviert ist

Der Patch ACSD-47232 behebt das Problem, dass der Coupon nicht angewendet wird, wenn **[!UICONTROL Same as Billing Address]** aktiviert ist. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23 installiert ist. Die Patch-ID ist ACSD-47232. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Coupon wird nicht angewendet, wenn **[!UICONTROL Same as Billing Address]** aktiviert ist.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie Adobe Commerce.
1. Einfaches Produkt mit Gewichtung erstellen = *8*.
1. Erstellen Sie einen neuen Kunden mit der standardmäßigen Abrechnungs- und Lieferadresse.
1. Erstellen Sie eine Preisregel für den Warenkorb mit einem Coupon.
   * In **[!UICONTROL Conditions]** Abschnitte hinzufügen *Gesamtgewicht größer/gleich 5*
1. Versuchen Sie, eine neue Bestellung im [!UICONTROL Commerce] Admin.
   * Verwenden des gerade erstellten Kunden
   * Produkt hinzufügen
   * Versuchen Sie, den Gutschein anzuwenden

<u>Erwartete Ergebnisse</u>:

Coupon wird angewendet.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten einen Fehler ähnlich dem folgenden: *Der Couponcode 123 ist ungültig. Überprüfen Sie den Code und versuchen Sie es erneut.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
