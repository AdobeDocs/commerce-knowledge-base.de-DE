---
title: 'ACSD-50345: reCAPTCHA-Probleme während des Checkouts'
description: Wenden Sie den ACSD-50345 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem die reCAPTCHA-v2- und -v3-Validierungen beim Aufgeben von Bestellungen und während des Checkouts fehlschlagen.
exl-id: ac8c8130-0e4d-4610-9a55-afa779cce7a0
feature: Checkout, Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# ACSD-50345: reCAPTCHA-Probleme während des Checkouts

Mit dem Patch ACSD-50345 wird das Problem behoben, dass die Validierungen von reCAPTCHA v2 und v3 beim Aufgeben von Bestellungen und während des Checkouts fehlschlagen. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.31 installiert ist. Die Patch-ID ist ACSD-50345. Beachten Sie, dass das Problem teilweise in Adobe Commerce 2.4.6 behoben wurde und in Adobe Commerce 2.4.7 vollständig behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.5-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

**#1**

Google reCAPTCHA v2 wird nach dem Übermitteln einer fehlgeschlagenen Zahlung nicht neu geladen.

<u>Schritte zur Reproduktion</u>

1. Konfigurieren Sie **[!UICONTROL Google reCAPTCHA v2]** (*bin kein Roboter*).
1. Aktivieren Sie die **[!UICONTROL reCAPTCHA]** für den Checkout.
1. Versuchen Sie, eine Bestellung aufzugeben, ohne auf **[!UICONTROL reCAPTCHA]** zu klicken.
1. Sobald der/die Benutzende die Fehlermeldung für das fehlende reCAPTCHA erhalten hat (*reCAPTCHA-Validierung fehlgeschlagen, bitte erneut versuchen*), auf das **[!UICONTROL reCAPTCHA]** klicken und dann versuchen, eine Bestellung aufzugeben.

<u>Erwartete Ergebnisse</u>

Die Bestellung wird nicht mit einem falschen reCAPTCHA aufgegeben.

<u>Tatsächliche Ergebnisse</u>

Es wird ein Fehler ausgelöst - *reCAPTCHA-Validierung fehlgeschlagen, erneut versuchen* und *Kein solcher Warenkorb mit ID = 4*

**#2**

Google reCAPTCHA v3 Invisible funktioniert nicht beim Checkout und die Bestellung kann nicht aufgegeben werden. `PlaceOrder` Ereignis wird nicht ausgelöst.

<u>Schritte zur Reproduktion</u>

1. Konfigurieren Sie die **[!UICONTROL reCAPTCHA v3 Invisible]** über die **[!UICONTROL Security]** **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > .
1. Aktivieren Sie **[!UICONTROL reCAPTCHA v3 Invisible]** für den Checkout/die Bestellung auf der Registerkarte **[!UICONTROL Storefront]** .
1. Versuchen Sie, eine Bestellung mit der [!UICONTROL Check/Money order] Zahlungsmethode aufzunehmen.

<u>Erwartete Ergebnisse</u>

Die Bestellung sollte bei eingeschaltetem **[!UICONTROL reCAPTCHA]** erfolgen.

<u>Tatsächliche Ergebnisse</u>

Nach dem Klicken auf die Schaltfläche &quot;**[!UICONTROL Place Order]**&quot; wird sie deaktiviert, und es passiert nichts weiter.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
