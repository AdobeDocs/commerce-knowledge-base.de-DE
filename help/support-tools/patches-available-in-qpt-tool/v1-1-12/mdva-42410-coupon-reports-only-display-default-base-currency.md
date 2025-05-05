---
title: 'MDVA-42410: In Couponberichten wird nur die Standard-Basiswährung angezeigt'
description: Der Patch MDVA-42410 behebt das Problem, dass die Couponberichte nur die Basiswährung anzeigen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-42410. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
exl-id: b442a2ce-1bd4-4f09-95fd-2c626e32f509
feature: Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-42410: In Couponberichten wird nur die Standard-Basiswährung angezeigt

Der Patch MDVA-42410 behebt das Problem, dass die Couponberichte nur die Basiswährung anzeigen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-42410. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

In Couponberichten wird nur die standardmäßige Basiswährung angezeigt.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine zusätzliche Website-, Store- und Store-Ansicht.
1. Legen Sie eine andere Währung für diese neue Website fest. Zum Beispiel Euro.
1. Wechseln Sie **Geschäfte** > **Währungskurse** und konfigurieren Sie die Währungskurse auf **Euro**.
1. Erstellen Sie **Warenkorb-Preisregel** mit einem bestimmten Coupon - **Test**.
1. Wechseln Sie zum Frontend und geben Sie auf der neuen Website eine Bestellung mit dem **Test**-Coupon auf.
1. Navigieren Sie **Berichte** > **Verkauf** > **Gutscheine**.
1. Wählen Sie die neue Website im Dropdown-Menü Umfang aus.
1. Statistiken aktualisieren und Berichte ausführen.

<u>Erwartete Ergebnisse</u>:

Couponberichte zeigen die Währung der neuen Website als Euro an.

<u>Tatsächliche Ergebnisse</u>:

Die standardmäßige Basiswährung (in diesem Fall USD) wird in Couponberichten für die neue Website verwendet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
