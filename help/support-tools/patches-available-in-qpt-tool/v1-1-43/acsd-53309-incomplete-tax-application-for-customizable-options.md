---
title: '"ACSD-53309: Unvollständiger Steuerantrag für anpassbare Optionen und [!UICONTROL Regular Price] label'''
description: Wenden Sie den Patch ACSD-53309 an, um das Adobe Commerce-Problem zu beheben, bei dem die Steuer in der Variablen[!UICONTROL Regular Price]", wenn eine anpassbare Option ausgewählt ist.
feature: Taxes, Shipping/Delivery
role: Admin, Developer
exl-id: de9b151e-6f92-4231-9e9f-4818c2961782
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-53309: Unvollständiger Steuerantrag für anpassbare Optionen und &#39;[!UICONTROL Regular Price]&#39; label

Der Patch ACSD-53309 behebt das Problem, dass die Steuer in der[!UICONTROL Regular Price]&quot;, wenn eine anpassbare Option ausgewählt ist. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 ist installiert. Die Patch-ID ist ACSD-53309. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Steuer wird nicht vollständig in der &quot;[!UICONTROL Regular Price]&quot;, wenn eine anpassbare Option ausgewählt wird.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich beim Admin-Bedienfeld an.
1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]** , um Steuereinstellungen zu konfigurieren.

   * [!UICONTROL Tax Classes]:

      * [!UICONTROL Tax Class for Shipping] = [!UICONTROL Taxable Goods]
      * [!UICONTROL Tax Class for Gift Options] = [!UICONTROL Taxable Goods]

   * [!UICONTROL Calculation Settings]:

      * [!UICONTROL Catalog Prices] = [!UICONTROL Including Tax]
      * [!UICONTROL Shipping Prices] = [!UICONTROL Including Tax]
      * [!UICONTROL Apply Discount On Prices] = [!UICONTROL Including Tax]

   * [!UICONTROL Default Tax Destination Calculation]:

      * [!UICONTROL Default Post Code] = *

   * [!UICONTROL Price Display Settings]:

      * [!UICONTROL Display Product Prices In Catalog] = [!UICONTROL Including Tax]
      * [!UICONTROL Display Shipping Prices] = [!UICONTROL Including Tax]

   * [!UICONTROL Shopping Cart Display Settings]:

      * [!UICONTROL Display Prices] = [!UICONTROL Including Tax]
      * [!UICONTROL Display Subtotal] = [!UICONTROL Including Tax]
      * [!UICONTROL Display Shipping Amount] = [!UICONTROL Including Tax]

1. Satz **[!UICONTROL Shipping Settings]** > **[!UICONTROL Origin]** > **[!UICONTROL Country]** = *Vereinigtes*.

1. Erstellen Sie Folgendes *[!UICONTROL Tax Rate]* und *[!UICONTROL Tax Rules]*:

   * [!UICONTROL Country] = Vereinigte Staaten
   * [!UICONTROL Zip Code] = *
   * [!UICONTROL State] = *
   * [!UICONTROL Rate] = 20 %
1. Erstellen Sie ein einfaches Produkt und legen Sie Folgendes fest:
   * [!UICONTROL Price = 110]
   * [!UICONTROL Special Price = 100]
   * Legen Sie in der Dropdown-Liste den Typ auf die benutzerdefinierte Option fest, wobei der Preis auf 15 % festgelegt ist
1. Gehen Sie zur Produktseite für das einfache Element, das auf der Storefront erstellt wurde.
1. Wählen Sie die erstellte benutzerdefinierte Option aus. *15 %*.

<u>Erwartete Ergebnisse</u>:

* Für die ausgewählte benutzerdefinierte Option wird eine 20-prozentige Steuer angewendet.
* &#39;[!UICONTROL Regular Price]&quot; = 151,80.

<u>Tatsächliche Ergebnisse</u>:

* Die 20 %-Steuer wird nicht auf die ausgewählte benutzerdefinierte Option angewendet.
* &#39;[!UICONTROL Regular Price]&quot; = 148,50.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
