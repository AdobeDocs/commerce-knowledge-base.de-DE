---
title: 'ACSD-53118: Regeln im Warenkorb mit Coupons funktionieren nicht richtig'
description: Wenden Sie den Patch ACSD-53118 an, um das Adobe Commerce-Problem zu beheben, bei dem die Warenkorbpreisregel mit einem Couponcode angewendet wird, während das Produkt im Warenkorb ein leeres Übereinstimmungsattribut aufweist.
feature: Shopping Cart, Price Rules
role: Admin, Developer
exl-id: a660ddb3-03fc-4460-b2a8-8e851f57e7a9
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-53118: Regeln im Warenkorb mit Coupons funktionieren nicht richtig

Mit dem Patch ACSD-53118 wird das Problem behoben, dass die Warenkorbpreisregel mit einem Couponcode angewendet wird, während das Produkt im Warenkorb ein leeres übereinstimmendes Attribut aufweist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41 installiert ist. Die Patch-ID ist ACSD-53118. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Warenkorbpreisregel wird mithilfe eines Couponcodes angewendet, während das Produkt im Warenkorb ein leeres übereinstimmendes Attribut aufweist.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein Preisattribut und fügen Sie es dem Attributsatz hinzu. Machen Sie das -Attribut in Promo-Regelbedingungen verwendbar.
1. Erstellen Sie ein Produkt und lassen Sie das neue Attribut leer.
1. Erstellen Sie eine Warenkorb-Preisregel mit einem bestimmten Coupon und der folgenden Bedingung:

   * Wenn ein Artikel im Warenkorb gefunden wird, für den alle folgenden Bedingungen erfüllt sind: Attribute1 ist 0.

1. Fügen Sie das in Schritt 2 erstellte Produkt zum Warenkorb hinzu.
1. Verwenden Sie den Couponcode für die in Schritt 3 erstellte Warenkorbregel.

<u>Erwartete Ergebnisse</u>:

Der Rabatt wird nicht auf den Warenkorb angewendet.

<u>Tatsächliche Ergebnisse</u>:

Der Rabatt wird auf den Warenkorb angewendet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
