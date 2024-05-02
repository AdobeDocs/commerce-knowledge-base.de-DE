---
title: "ACSD-55241: **Verwendet** und **Verwendete Zeiten** Attribute zeigen falsche Werte für generierte Gutscheine an."
description: Wenden Sie den Patch ACSD-55241 an, um das Adobe Commerce-Problem zu beheben, bei dem die Attribute **Verwendet** und **Verwendete Zeiten** falsche Werte für generierte Gutscheine anzeigen
feature: Price Rules
role: Admin, Developer
exl-id: cfe0f8af-423a-4e12-a332-053392cbabed
source-git-commit: 5d0b4743fe49d22c099102490f93dc4065ab4413
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# ACSD-55241: **Verwendet** und **Verwendete Zeiten** -Attribute zeigen falsche Werte für generierte Gutscheine an

Der Patch ACSD-55241 behebt das Problem, bei dem das **Verwendet** und **Verwendete Zeiten** -Attribute zeigen falsche Werte für generierte Gutscheine an. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.47 ist installiert. Die Patch-ID ist ACSD-55241. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

**Verwendet** und **Verwendete Zeiten** -Attribute zeigen falsche Werte für generierte Gutscheine an.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen **[!UICONTROL Cart Price Rules]** von **[!UICONTROL Admin]** > **[!UICONTROL Marketing]** > **[!UICONTROL Promotion]** und fügen Sie alle Bedingungen hinzu, die bei der Bestellung übereinstimmen (Beispiel: Zwischensumme größer als *5$*)

* Wenden Sie einen Rabatt an.
* Auswählen **[!UICONTROL Auto Coupon]**.
* Sie generiert einige Coupon-Codes aus **Coupon-Codes verwalten**.
* Neuindizieren und leeren Sie den Cache.

1. Erstellen Sie eine **[!UICONTROL customer account]** und sich in das Frontend einloggen.
1. Ein Produkt mit mehr als *2* die Mengen im Warenkorb und einen Gutschein anwenden.
1. Klicken Sie auf **[!UICONTROL Check Out with Multiple Addresses]**.
1. Wählen Sie für jede Menge eine separate Adresse aus, geben Sie die Bestellung auf und schließen Sie den Checkout-Prozess ab.
1. Beobachten Sie die Bestellsumme vom Administrator und sehen Sie sich den angewendeten Rabatt an.
1. Platzieren Sie eine weitere Bestellung mit einem anderen Gutschein.
1. Führen Sie die `php81 bin/Magento queue:consumers: start sales.rule.update.coupon.usage &` -Befehl, um die Nutzung des Gutscheincodes zu aktualisieren.

<u>Erwartete Ergebnisse</u>:

Die richtige Anzahl sollte in der **Verwendete Zeit** und **Verwendet** Spalten mit **Ja** Wert für **[!UICONTROL manage coupon]** im **[!UICONTROL cart price rule]** im Admin.

<u>Tatsächliche Ergebnisse</u>:

Die Anzahl der verwendeten Gutscheincodes wird im **Verwendete Zeit** im Coupons-Raster und dem **Verwendet** zeigt die Spalte *Nein* Wert, wenn Sie eine Bestellung mit mehreren Versandadressen aufgeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
