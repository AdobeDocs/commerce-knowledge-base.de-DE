---
title: '"ACSD-47920: Ein Gastbenutzer kann Bestellungen auch dann über die REST-API aufgeben, wenn [!UICONTROL Allow Guest Checkout] is off'''
description: Wenden Sie den Patch ACSD-47920 an, um das Adobe Commerce-Problem zu beheben, bei dem Bestellungen auch dann über die REST-API als Gastbenutzer platziert werden können, wenn die [!UICONTROL Allow Guest Checkout] deaktiviert ist.
exl-id: 8726eac4-ab19-4232-8e15-270d09bdc0a5
feature: REST, Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-47920: Ein Gastbenutzer kann Bestellungen auch dann über die REST-API aufgeben, wenn **[!UICONTROL Allow Guest Checkout]** ist deaktiviert

Der Patch ACSD-47920 behebt das Problem, dass Bestellungen auch dann über die REST-API als Gastbenutzer aufgegeben werden können, wenn die **[!UICONTROL Allow Guest Checkout]** deaktiviert ist. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 ist installiert. Die Patch-ID ist ACSD-47920. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Bestellungen können auch dann über die REST-API als Gastbenutzer platziert werden, wenn die **[!UICONTROL Allow Guest Checkout]** deaktiviert ist.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu Adobe Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** > und legen Sie die **[!UICONTROL Allow Guest Checkout]** nach _Nein_.
1. Verwenden Sie die REST-API, um einem Warenkorb ein Produkt hinzuzufügen und eine Bestellung aufzugeben.

<u>Erwartete Ergebnisse</u>:

Die Checkout-API gibt einen Fehler zurück *[!UICONTROL Sorry, guest checkout is not available]* if **[!UICONTROL Allow Guest Checkout]** auf _Nein_.

<u>Tatsächliche Ergebnisse</u>:

Die Checkout-API ermöglicht die Platzierung einer Bestellung auch dann, wenn **[!UICONTROL Allow Guest Checkout]** auf _Nein_.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
