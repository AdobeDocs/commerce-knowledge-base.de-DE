---
title: "ACSD-45754: Belohnungspunkte, die nach Anwendung des Gutscheins auf den Warenkorb nicht hinzugefügt wurden"
description: Der Patch ACSD-45754 behebt das Problem, dass nach dem Anwenden eines Gutscheins auf den Warenkorb keine Belohnungspunkte hinzugefügt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 installiert ist. Die Patch-ID ist ACSD-45754. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.
exl-id: 957713c0-3e2e-4dc9-8924-2ae84c817e47
feature: Orders, Rewards, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# ACSD-45754: Bonuspunkte, die nach Anwendung des Gutscheins auf den Warenkorb nicht hinzugefügt wurden

Der Patch ACSD-45754 behebt das Problem, dass nach dem Anwenden eines Gutscheins auf den Warenkorb keine Belohnungspunkte hinzugefügt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 installiert ist. Die Patch-ID ist ACSD-45754. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.1 - 2.4.5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Nach dem Anwenden eines Gutscheins auf den Warenkorb werden keine Prämienpunkte hinzugefügt.

<u>Voraussetzungen</u>:

PayPal Zahlungsmethode ist konfiguriert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie die Rewards-Punktwechselkurse, indem Sie zu **Store** > **Sonstige Einstellungen** > **Rewards-Wechselkurse** navigieren.
1. Erstellen Sie eine Preisregel für den Warenkorb mit einem Coupon-Code, um 100 Bonuspunkte für angemeldete Kunden anzuwenden.
1. Sehen Sie sich ein Produkt als angemeldeten Kunden mit PayPal und dem Couponcode an.
1. Überprüfen Sie den Verlauf der Belohnungspunkte unter dem Kundenkonto im Admin.

<u>Erwartete Ergebnisse</u>:

Prämienpunkte werden dem Kunden gemäß der Preisregel hinzugefügt.

<u>Tatsächliche Ergebnisse</u>:

Dem Kunden werden keine Belohnungspunkte hinzugefügt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) verfügbar sind, in unserer Entwicklerdokumentation.
