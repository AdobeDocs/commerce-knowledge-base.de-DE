---
title: "ACSD-46617: **[!UICONTROL Continue to Checkout]** Schaltfläche grau ausgeblendet, wenn die Zwischensumme größer als der konfigurierte Mindestauftragsbetrag ist."
description: Wenden Sie den Patch ACSD-46617 an, um das Adobe Commerce-Problem zu lösen, bei dem die Schaltfläche **[!UICONTROL Continue to Checkout]** ausgegraut ist, selbst wenn die Zwischensumme größer als der konfigurierte Mindestbestellbetrag ist.
exl-id: 42fe02bd-f48b-4c6d-8643-ea2c1aa98c94
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-46617: Schaltfläche &quot;[!UICONTROL Continue to Checkout]&quot; ausgegraut, wenn die Zwischensumme größer als &quot;[!UICONTROL Minimum Order Amount]&quot; ist

Dieser Patch ACSD-46617 behebt das Problem, dass die Schaltfläche **[!UICONTROL Continue to Checkout]** ausgegraut ist, selbst wenn die Zwischensumme größer als der konfigurierte Mindestbestellbetrag ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 installiert ist. Die Patch-ID ist ACSD-46617. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Schaltfläche **[!UICONTROL Continue to Checkout]** ist grau ausgeblendet, selbst wenn die Zwischensumme größer als der konfigurierte Mindestbestellbetrag ist.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu Adobe Commerce Admin > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Minimum Order Amount]** und legen Sie Folgendes fest:
   * [!UICONTROL Enable]: *[!UICONTROL Yes]*
   * 
     [!UICONTROL Minimum Amount]: *2*

1. Erstellen Sie eine [!UICONTROL Cart Price Rule].
   * [!UICONTROL Coupon Code]: *[!UICONTROL TEST (optional)]*
   * [!UICONTROL Conditions]: *[!UICONTROL Keep empty]*
   * [!UICONTROL Actions]:
      * [!UICONTROL Apply]: *[!UICONTROL Percent of product price discount]*
      * 
        [!UICONTROL Discount Amount]: *92*
      * [!UICONTROL Apply to Shipping Amount]: *[!UICONTROL Yes]*
1. Erstellen Sie ein Produkt mit einem Preis von 25 USD.
1. Fügen Sie das Produkt zum Warenkorb hinzu.
1. Gehen Sie zum Warenkorb, wählen Sie die Methode $5 **[!UICONTROL Flat Rate shipping]** aus und wenden Sie den Gutscheincode an.
1. Gehen Sie zum Checkout, schließen Sie den Versand ab und navigieren Sie zum Abschnitt **[!UICONTROL Paytment]** .
1. Gehen Sie zurück zum Warenkorb.

<u>Erwartete Ergebnisse</u>:

Im Zusammenhang mit dem Mindestbestellbetrag gibt es keinen Fehler, da die Gesamtsumme von 2,4 USD den erforderlichen Betrag von 2 USD übersteigt.

<u>Tatsächliche Ergebnisse</u>:

* Im Zusammenhang mit dem Mindestbestellbetrag tritt ein Fehler auf, selbst wenn die Gesamtsumme von 2,4 USD den Mindestbestellbetrag von 2 USD übersteigt.
* Die Schaltfläche **[!UICONTROL Continue to Checkout]** ist grau ausgeblendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
