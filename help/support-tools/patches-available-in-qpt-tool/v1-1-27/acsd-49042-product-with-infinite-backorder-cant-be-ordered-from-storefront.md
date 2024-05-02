---
title: "ACSD-49042: Produkt mit unendlichem Backorder kann nicht von der Storefront bestellt werden"
description: Wenden Sie den Patch ACSD-49042 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Produkt mit unendlichem Backorder nicht über die Storefront bestellt werden kann.
exl-id: b9227296-f300-447c-a241-30ccc0691c9a
feature: Admin Workspace, Orders, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-49042: Produkt mit unendlichem Backorder kann nicht von der Storefront bestellt werden

Der Patch ACSD-49042 behebt das Problem, dass ein Produkt mit unendlichem Backorder nicht über die Storefront bestellt werden kann. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 ist installiert. Die Patch-ID lautet ACSD-49042. Beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Fehler tritt auf, wenn ein Produkt mit unendlichem Backorder nicht über die Storefront bestellt werden kann.

<u>Zu reproduzierende Schritte</u>:

1. Legen Sie die folgenden Konfigurationseinstellungen fest:
   * **[!UICONTROL Display Out of Stock Products]** auf *[!UICONTROL Yes]*.
   * **[!UICONTROL Backorders]** auf *[!UICONTROL Allow Qty Below 0]*.
1. Hinzufügen neuer **[!DNL custom stock]** und **[!DNL custom source]**.
1. Zuweisen eines Produkts zum **[!DNL custom source]** und stellen Sie sicher, dass dafür eine Inventarnummer festgelegt ist (z. B.: *10*).
1. Öffnen Sie auf der Produktebearbeitungsseite **[!UICONTROL Advanced Inventory]**. Legen Sie die **[!UICONTROL minimum quantity]** im Warenkorb (Beispiel: *160*). Die Menge muss über dem Bestand liegen.
1. Gehen Sie zur Storefront und kaufen Sie ein Produkt, um eine Reservierung zu erstellen.
1. Ändern Sie die **[!UICONTROL product quantity]** nach *0*. Der entscheidende Punkt besteht darin, das Produkt aus dem **[!DNL Admin panel]** bei einer Reservierung.
1. Öffnen Sie die **[!UICONTROL product page]** auf der Storefront und versuchen Sie, das Produkt zum Warenkorb hinzuzufügen.

<u>Erwartete Ergebnisse</u>:

Es ist möglich, das Produkt zum Warenkorb hinzuzufügen, da Rückstände für eine Menge unter *0* sind erlaubt.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt wird als nicht vorrätig angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
