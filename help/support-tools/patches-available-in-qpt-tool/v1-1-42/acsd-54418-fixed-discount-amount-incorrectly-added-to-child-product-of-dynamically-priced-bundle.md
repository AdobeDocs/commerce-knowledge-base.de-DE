---
title: "ACSD-54418: Fester Abzinsungsbetrag wurde fälschlicherweise zum untergeordneten Produkt des dynamisch primierten Bundles hinzugefügt."
description: Wenden Sie den Patch ACSD-54418 an, um das Adobe Commerce-Problem zu beheben, bei dem der feste Abzinsungsbetrag fälschlicherweise auf jedes untergeordnete Produkt des dynamisch primitierten Bundles angewendet wird.
feature: Shopping Cart
role: Admin, Developer
exl-id: f9a00a4b-0a57-4a61-8b7c-6385e0751991
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-54418: Fester Rabattbetrag wurde fälschlicherweise zum untergeordneten Produkt des dynamisch preisgekrönten Bundles hinzugefügt.

Der Patch ACSD-54418 behebt das Problem, bei dem der feste Rabattbetrag fälschlicherweise auf jedes untergeordnete Produkt des dynamisch preisgekrönten Bundles angewendet wird. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.42 ist installiert. Die Patch-ID lautet ACSD-54418. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben ist.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der feste Abzinsungsbetrag wird fälschlicherweise auf jedes untergeordnete Produkt des dynamisch preisgekrönten Bundles angewendet.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine **[!UICONTROL bundle product]** mit dynamischen Preisen und *2* Bundle-Optionen
1. Erstellen Sie eine **[!UICONTROL cart price rule]** mit einem bestimmten Gutscheincode, der nur für das gebündelte Produkt gilt **[!UICONTROL SKU]** und hat einen festen Rabatt.
1. Fügen Sie das gebündelte Produkt zum Warenkorb hinzu.
1. Wenden Sie die **[!UICONTROL coupon code]**.
1. Überprüfen Sie den Rabatt, der auf den Warenkorb angewendet wird.

<u>Erwartete Ergebnisse</u>:

Der Rabatt wird nur einmal auf das gesamte gebündelte Produkt angewendet.

<u>Tatsächliche Ergebnisse</u>:

Der Rabatt wird auf jedes untergeordnete Paket angewendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
