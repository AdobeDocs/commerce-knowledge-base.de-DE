---
title: '"ACSD-51735: Bestellelementstatus falsch auf * gesetzt[!UICONTROL Ordered]* wenn der Produktbestand 0'' ist'
description: Wenden Sie den Patch ACSD-51735 an, um das Adobe Commerce-Problem zu beheben, bei dem der Bestellelementstatus fälschlicherweise auf * gesetzt ist.[!UICONTROL Ordered]* wenn der Produktbestand 0 beträgt.
feature: Orders, Products
role: Admin
exl-id: c6376698-71dc-46b8-a5b2-86dc26a574ab
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-51735: Bestellelementstatus falsch auf gesetzt *[!UICONTROL Ordered]* wenn der Produktbestand 0 ist

Der Patch ACSD-51735 behebt das Problem, bei dem der Bestellelementstatus fälschlicherweise auf *[!UICONTROL Ordered]* wenn der Produktbestand 0 beträgt. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 installiert ist. Die Patch-ID ist ACSD-50895. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Bestellelementstatus wurde fälschlicherweise auf *[!UICONTROL Ordered]* wenn der Produktbestand 0 beträgt.

<u>Voraussetzungen</u>:

* Adobe Commerce Inventory management (MSI)-Module sind installiert.
* Rückläufe sind in **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** > **[!UICONTROL Backorders]**.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein neues Lager.
1. Erstellen Sie eine neue Quelle.
1. Weisen Sie dem neuen Lager die Standardwebsite zu und weisen Sie die neue Quelle zu.
1. Erstellen Sie ein neues Produkt.

   * Legen Sie die Standardquellqualität auf 10 und die neue Quellqualität auf 0 fest.

1. Fügen Sie das Produkt dem Warenkorb auf der Storefront hinzu.
1. Beobachten Sie die Hintergrundwarnung beim Checkout und geben Sie an, dass das Produkt aus einer neuen Quelle stammt.
1. Platzieren Sie die Bestellung.
1. Öffnen Sie die Bestellung in Admin und überprüfen Sie den Status der Aufstockung.

<u>Erwartete Ergebnisse</u>:

Die Reihenfolge zeigt an, dass die Menge 1 in umgekehrter Reihenfolge angeordnet ist.

<u>Tatsächliche Ergebnisse</u>:

Die Reihenfolge zeigt, dass die Menge 1 geordnet ist, nicht umgekehrt.

>[!MORELIKETHIS]
>
>[Der Bestellelementstatus wurde fälschlicherweise auf *[!UICONTROL Backordered]*](/help/support-tools/patches-available-in-qpt-tool/v1-1-33/acsd-51408-order-item-status-is-set-to-backordered.md)

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
