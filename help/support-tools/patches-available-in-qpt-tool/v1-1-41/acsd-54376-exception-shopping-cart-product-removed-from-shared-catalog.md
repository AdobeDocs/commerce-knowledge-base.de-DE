---
title: 'ACSD-54376: Ausnahme im Warenkorb, wenn Produkt aus [!UICONTROL shared catalog] entfernt wurde'
description: Wenden Sie den Patch ACSD-54376 an, um das Adobe Commerce-Problem zu beheben, bei dem im Warenkorb eine Ausnahme auftritt, wenn ein Produkt aus dem [!UICONTROL shared catalog] entfernt wird, nachdem es zum Warenkorb hinzugefügt wurde.
feature: Shopping Cart, B2B
role: Admin, Developer
exl-id: a1e5c084-532f-49e8-ab87-6674b44218e8
source-git-commit: 1cc565d5888e5a380c04879d9aced2c19e92c2e5
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-54376: Ausnahme im Warenkorb, wenn Produkt aus [!UICONTROL shared catalog] entfernt wurde

Der Patch ACSD-54376 behebt das Problem, dass im Warenkorb eine Ausnahme auftritt, wenn ein Produkt aus dem [!UICONTROL shared catalog] entfernt wird, nachdem es zum Warenkorb hinzugefügt wurde. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41 installiert ist. Die Patch-ID ist ACSD-54376. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Eine Ausnahme tritt im Warenkorb auf, wenn ein Produkt aus dem [!UICONTROL shared catalog] entfernt wird, nachdem es zum Warenkorb hinzugefügt wurde.

<u>Schritte zur Reproduktion</u>:

1. Installieren von Adobe Commerce mit B2B.
1. [!UICONTROL shared catalog] aktivieren.
1. Erstellen Sie ein Produkt und weisen Sie es dem [!UICONTROL shared catalog] zu.
1. Fügen Sie ein Produkt aus der Storefront zum Warenkorb hinzu.
1. Entfernen Sie das Produkt aus dem [!UICONTROL shared catalog].
1. Navigieren Sie über die Dropdown-Liste Mini-Warenkorb zur Checkout-Seite.

<u>Erwartete Ergebnisse</u>:

Ausnahmen werden behandelt und nicht angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Auf der Kaufbestätigungsseite wird eine nicht behandelte Ausnahme angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
