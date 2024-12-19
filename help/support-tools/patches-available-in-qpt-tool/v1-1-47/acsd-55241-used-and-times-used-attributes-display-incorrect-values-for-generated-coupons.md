---
title: 'ACSD-55241: **Verwendet** und **Verwendete** Attribute zeigen falsche Werte für generierte Coupons an'
description: Wenden Sie den Patch ACSD-55241 an, um das Adobe Commerce-Problem zu beheben, bei dem die Attribute **Verwendet** und **Verwendet** falsche Werte für generierte Coupons anzeigen
feature: Price Rules
role: Admin, Developer
exl-id: cfe0f8af-423a-4e12-a332-053392cbabed
source-git-commit: f830486ab3b00fca92dda897bbf0bfbae41543c1
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# ACSD-55241: **Verwendet** und **Verwendet**-Attribute zeigen falsche Werte für generierte Coupons an

Der Patch ACSD-55241 behebt das Problem, dass die Attribute **Verwendet** und **Verwendet** falsche Werte für generierte Coupons anzeigen. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.47 installiert ist. Die Patch-ID ist ACSD-55241. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Attribute **Verwendet** und **Verwendet** zeigen falsche Werte für generierte Coupons an.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie **[!UICONTROL Cart Price Rules]** aus **[!UICONTROL Admin]** > **[!UICONTROL Marketing]** > **[!UICONTROL Promotion]** und fügen Sie alle Bedingungen hinzu, die bei der Bestellung übereinstimmen (Beispiel: Zwischensumme größer als *5$*)

   * Beliebigen Rabatt anwenden.
   * Wählen Sie **[!UICONTROL Auto Coupon]** aus.
   * Es werden einige Couponcodes aus &quot;**verwalten“**.
   * Indizieren und bereinigen Sie den Cache.

1. Erstellen Sie eine **[!UICONTROL customer account]** und melden Sie sich beim Frontend an.
1. Fügen Sie ein Produkt mit mehr als *2 %* Warenkorb hinzu und verwenden Sie einen Gutschein.
1. Klicken Sie auf **[!UICONTROL Check Out with Multiple Addresses]**.
1. Wählen Sie für jede Menge eine separate Adresse aus, geben Sie die Bestellung auf und schließen Sie den Checkout-Prozess ab.
1. Beobachten Sie die Bestellsumme von der Administratorin bzw. dem Administrator und sehen Sie sich den angewendeten Rabatt an.
1. Geben Sie eine weitere Bestellung mit einem anderen Coupon auf.
1. Führen Sie den Befehl `php81 bin/Magento queue:consumers: start sales.rule.update.coupon.usage &` aus, um die Verwendung des Gutscheincodes zu aktualisieren.

<u>Erwartete Ergebnisse</u>:

Die richtige Anzahl sollte in den Spalten **Verwendete Zeit** und **Verwendet** mit dem Wert **Ja** für **[!UICONTROL manage coupon]** in der **[!UICONTROL cart price rule]** in der Admin-Liste angezeigt werden.

<u>Tatsächliche Ergebnisse</u>:

Die Anzahl der verwendeten Couponcodes wird nicht in der Spalte **Verwendete Zeit** im Couponraster aktualisiert, und die Spalte **Verwendet** zeigt den Wert *Nein* an, wenn Sie eine Bestellung mit mehreren Versandadressen aufgeben.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
