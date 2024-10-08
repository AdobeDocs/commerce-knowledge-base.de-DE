---
title: "ACSD-58163: [!UICONTROL Cart Price Rule] wendet keinen Rabatt vom übereinstimmenden [!UICONTROL Customer Segment] Warenkorb ohne Couponcode an"
description: Wenden Sie den Patch ACSD-58163 an, um das Adobe Commerce-Problem zu beheben, bei dem der [!UICONTROL Cart Price Rule] keinen Rabatt für einen Gast vom entsprechenden [!UICONTROL Customer Segment] Warenkorb ohne Couponcode anwendet.
feature: Products
role: Admin, Developer
source-git-commit: 7603a482953dc0ac0784ab6e6d3b22e4245e3e75
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---


# ACSD-58163: [!UICONTROL Cart Price Rule] wendet keinen Rabatt vom übereinstimmenden [!UICONTROL Customer Segment] Warenkorb ohne Couponcode an

Der Patch ACSD-58163 behebt das Problem, dass der [!UICONTROL Cart Price Rule] keinen Rabatt vom entsprechenden [!UICONTROL Customer Segment] Warenkorb ohne Couponcode anwendet. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 installiert ist. Die Patch-ID ist ACSD-58163. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.5.0 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

[!UICONTROL Cart Price Rule] wendet für einen Gast keinen Rabatt vom entsprechenden [!UICONTROL Customer Segment] Warenkorb ohne Couponcode an.

<u>Zu reproduzierende Schritte</u>:

1. Kundensegment erstellen:
   * Für Besucher.
   * Mit der Bedingung, dass ein Produkt im Warenkorb ist.

1. Erstellen Sie eine *[!UICONTROL Cart Price Rule]*:
   * Ohne Couponcode.
   * Mit der Bedingung, die mit dem Besucher-Kundensegment übereinstimmt.

1. Erstellen Sie ein einfaches Produkt.
1. Öffnen Sie die Storefront als Gast.
1. Fügen Sie dem Warenkorb ein einfaches Produkt hinzu.
1. Gehen Sie zum Warenkorb.

<u>Erwartete Ergebnisse</u>:

*[!UICONTROL Cart Price Rule]* Rabatt wird angewendet.

<u>Tatsächliche Ergebnisse</u>:

*[!UICONTROL Cart Price Rule]* Rabatt wird nicht angewendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
