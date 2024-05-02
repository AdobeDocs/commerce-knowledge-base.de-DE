---
title: "ACSD-52786: Katalogregel *[!UICONTROL SKU is]* gilt für alle Produkte, die mit der SKU beginnen."
description: Wenden Sie den Patch ACSD-52786 an, um das Adobe Commerce-Problem zu beheben, bei dem die Bedingung der Katalogregel *[!UICONTROL SKU is]* gilt für alle Produkte, die mit der jeweiligen SKU beginnen.
feature: Price Rules
role: Admin
exl-id: af373b6c-5944-412b-a544-cc6fc3f209d3
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-52786: Katalogregel &quot;*[!UICONTROL SKU is]*&quot;gilt für alle Produkte, die mit der SKU beginnen.

Der Patch ACSD-52786 behebt das Problem, bei dem die Bedingung der Katalogregel *[!UICONTROL SKU is]* gilt für alle Produkte, die mit der jeweiligen SKU beginnen. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-52786. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Bedingung für Katalogregel *[!UICONTROL SKU is]* gilt für alle Produkte, die mit der jeweiligen SKU beginnen.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie zwei Produkte, eines mit SKU &quot;24&quot;und eines mit SKU &quot;24-MB01&quot;.
1. Navigieren Sie zu **[!UICONTROL Marketing]** > **[!UICONTROL Catalog Price Rule]** > **[!UICONTROL Add New Rule]**.
1. Wenden Sie die folgende Bedingung an:
   * *[!UICONTROL If ** ALL **dieser Bedingungen** TRUE **]*: *[!UICONTROL SKU is 24]*
1. Legen Sie in Aktionen einen beliebigen Rabattbetrag fest.
1. Klicks **[!UICONTROL Save and Apply]**.
1. Leeren Sie den Cache.
1. Gehen Sie zur Storefront und überprüfen Sie den Preis von 24 MB01.

<u>Erwartete Ergebnisse</u>:

Katalogregel wird nur auf ein einzelnes Produkt mit einer SKU von 24 angewendet.

<u>Tatsächliche Ergebnisse</u>:

Bedingung für Katalogregel *[!UICONTROL SKU is]* gilt für alle Produkte, die mit der jeweiligen SKU beginnen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
