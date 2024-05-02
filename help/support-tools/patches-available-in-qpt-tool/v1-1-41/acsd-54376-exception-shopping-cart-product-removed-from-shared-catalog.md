---
title: '"ACSD-54376: Ausnahme im Warenkorb, wenn Produkt aus entfernt wurde [!UICONTROL shared catalog]'''
description: Wenden Sie den Patch ACSD-54376 an, um das Adobe Commerce-Problem zu beheben, bei dem eine Ausnahme im Warenkorb auftritt, wenn ein Produkt aus dem Warenkorb entfernt wird. [!UICONTROL shared catalog] nach dem Hinzufügen zum Warenkorb.
feature: Shopping Cart, B2B
role: Admin, Developer
exl-id: a1e5c084-532f-49e8-ab87-6674b44218e8
source-git-commit: 1cc565d5888e5a380c04879d9aced2c19e92c2e5
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-54376: Ausnahme im Warenkorb, wenn das Produkt aus entfernt wurde [!UICONTROL shared catalog]

Der Patch ACSD-54376 behebt das Problem, dass im Warenkorb eine Ausnahme auftritt, wenn ein Produkt aus dem Warenkorb entfernt wird. [!UICONTROL shared catalog] nach dem Hinzufügen zum Warenkorb. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41 installiert ist. Die Patch-ID ist ACSD-54376. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Im Warenkorb tritt eine Ausnahme auf, wenn ein Produkt aus dem [!UICONTROL shared catalog] nach dem Hinzufügen zum Warenkorb.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie Adobe Commerce mit B2B.
1. Aktivieren [!UICONTROL shared catalog].
1. Erstellen Sie ein Produkt und weisen Sie es dem Standard zu. [!UICONTROL shared catalog].
1. Fügen Sie dem Warenkorb ein Produkt aus der Storefront hinzu.
1. Entfernen Sie das Produkt aus der [!UICONTROL shared catalog].
1. Navigieren Sie über das Dropdown-Menü &quot;Mini-Warenkorb&quot;zur Checkout-Seite.

<u>Erwartete Ergebnisse</u>:

Ausnahmen werden bearbeitet und Ihnen nicht angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Eine nicht verarbeitete Ausnahme wird auf der Checkout-Seite angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
