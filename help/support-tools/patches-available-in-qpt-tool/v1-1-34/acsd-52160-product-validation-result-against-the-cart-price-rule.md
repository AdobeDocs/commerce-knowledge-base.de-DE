---
title: "ACSD-52160: Ergebnis der Produktvalidierung anhand der Preisregel des Warenkorbs"
description: Wenden Sie den Patch ACSD-52160 an, um das Adobe Commerce-Problem zu beheben, bei dem das Ergebnis der Produktvalidierung anhand der Preisregel für den Warenkorb nicht ordnungsgemäß anhand der Regelbedingung ausgewertet wird *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*.
exl-id: a371c539-4440-4c84-baa4-774c32f66e41
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-52160: Das Ergebnis der Produktvalidierung mit der Warenkorbpreisregel wird nicht ordnungsgemäß ausgewertet

Der Patch ACSD-52160 behebt das Problem, dass das Ergebnis der Produktvalidierung anhand der Preisregel für den Warenkorb nicht ordnungsgemäß anhand der Regelbedingung ausgewertet wird. *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34 ist installiert. Die Patch-ID ist ACSD-52160. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Ergebnis der Produktvalidierung anhand der Regel zum Warenkorbpreis wird nicht ordnungsgemäß anhand der Regelbedingung ausgewertet. *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie zwei Produkte, die zwei verschiedenen Kategorien zugeordnet sind.
1. Erstellen Sie eine **[!UICONTROL Cart Price Rule]** mit Bedingungen wie:

   * **SKU 1** im *[!UICONTROL FOUND]* parameter
   * **SKU 2** im *[!UICONTROL NOT FOUND]* parameter

1. Fügen Sie beide Produkte zum Warenkorb hinzu.
1. Wenden Sie den Gutscheincode an.

<u>Erwartete Ergebnisse</u>

Der Couponcode wird nicht angewendet, da der Warenkorb Produkte der eingeschränkten Kategorie enthält.

<u>Tatsächliche Ergebnisse</u>

Der Couponcode wird angewendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) im [!DNL Quality Patches Tool] Handbuch.
