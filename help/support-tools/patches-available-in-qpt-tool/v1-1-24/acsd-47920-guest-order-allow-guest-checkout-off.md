---
title: 'ACSD-47920: Ein Gastbenutzer kann Bestellungen über die REST-API aufgeben, selbst wenn die [!UICONTROL Allow Guest Checkout] deaktiviert ist'
description: Wenden Sie den Patch ACSD-47920 an, um das Adobe Commerce-Problem zu beheben, bei dem Bestellungen als Gastbenutzer über die REST-API aufgegeben werden können, selbst wenn die [!UICONTROL Allow Guest Checkout] deaktiviert ist.
exl-id: 8726eac4-ab19-4232-8e15-270d09bdc0a5
feature: REST, Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-47920: Ein Gastbenutzer kann Bestellungen über die REST-API aufgeben, selbst wenn die **[!UICONTROL Allow Guest Checkout]** deaktiviert ist

Mit dem Patch ACSD-47920 wird das Problem behoben, dass Bestellungen als Gastbenutzer über die REST-API selbst dann aufgegeben werden können, wenn die **[!UICONTROL Allow Guest Checkout]** deaktiviert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 installiert ist. Die Patch-ID ist ACSD-47920. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Bestellungen können über die REST-API auch dann als Gastbenutzer aufgegeben werden, wenn die **[!UICONTROL Allow Guest Checkout]** deaktiviert ist.

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie zu Adobe Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** > und legen Sie die **[!UICONTROL Allow Guest Checkout]** auf _Nein_ fest.
1. Verwenden Sie die REST-API, um ein Produkt zu einem Warenkorb hinzuzufügen und eine Bestellung aufzugeben.

<u>Erwartete Ergebnisse</u>:

Die Gast-Checkout-API gibt eine *[!UICONTROL Sorry, guest checkout is not available]* zurück, wenn **[!UICONTROL Allow Guest Checkout]** auf &quot;_&quot;_.

<u>Tatsächliche Ergebnisse</u>:

Mit der Gast-Checkout-API kann eine Bestellung auch dann aufgegeben werden, wenn **[!UICONTROL Allow Guest Checkout]** auf &quot;_&quot;_.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
