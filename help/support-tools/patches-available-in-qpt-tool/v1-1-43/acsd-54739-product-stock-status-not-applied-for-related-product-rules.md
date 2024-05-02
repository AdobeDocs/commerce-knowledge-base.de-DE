---
title: '"ACSD-54739: *[!UICONTROL Product Stock]* Status nicht angewendet für *[!UICONTROL Related Product Rules]*'''
description: Wenden Sie den Patch ACSD-54739 an, um das Adobe Commerce-Problem zu beheben, bei dem *[!UICONTROL Product Stock]* Status wird nicht auf * angewendet[!UICONTROL Related Product Rules]*.
feature: Products
role: Admin, Developer
exl-id: 7bc106b1-2c97-46a1-8bb6-71b99511e480
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# ACSD-54739: *[!UICONTROL Product stock]* Status nicht beantragt *[!UICONTROL Related Product Rules]*

Der Patch ACSD-54739 behebt das Problem, bei dem der *[!UICONTROL Product stock]* Der Status wird nicht angewendet für *[!UICONTROL Related Product Rules]*. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 ist installiert. Die Patch-ID ist ACSD-54739. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

*[!UICONTROL Product stock]* Der Status wird nicht angewendet für *[!UICONTROL Related Product Rules]*.

<u>Zu reproduzierende Schritte</u>:

1. Legen Sie die **[!UICONTROL Display Out of Stock Products]** Konfiguration auf *Ja*.
1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** > **[!UICONTROL Search quantity attribute]** und *Ja* für die Bedingung der Angebotsregel.
1. Erstellen Sie die zugehörige Produktregel. Navigieren Sie zu **[!UICONTROL Product rule information]** > **[!UICONTROL Products to match]** > Fügen Sie eine Bedingung mit der Attributmenge hinzu (wählen Sie &quot;Vorrätig/nicht vorrätig&quot;aus).
1. Überprüfen Sie die Produkte am Frontend.

<u>Erwartete Ergebnisse</u>:

Das vorrätige/nicht vorrätige Produkt stimmt mit *[!UICONTROL Related Product Rules]*.

<u>Tatsächliche Ergebnisse</u>:

Das vorrätige/nicht vorrätige Produkt stimmt nicht mit der *[!UICONTROL Related Product Rules]*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
