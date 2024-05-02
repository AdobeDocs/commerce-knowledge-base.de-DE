---
title: "ACSD-50345: reCAPTCHA-Probleme beim Checkout"
description: Wenden Sie den Patch ACSD-50345 an, um das Adobe Commerce-Problem zu beheben, bei dem die reCAPTCHA v2- und v3-Validierungen beim Bestellen von Bestellungen und während des Checkouts fehlschlagen.
exl-id: ac8c8130-0e4d-4610-9a55-afa779cce7a0
feature: Checkout, Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# ACSD-50345: reCAPTCHA-Probleme beim Checkout

Der Patch ACSD-50345 behebt das Problem, bei dem die reCAPTCHA v2- und v3-Validierungen bei der Auftragserteilung und beim Checkout fehlschlagen. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.31 installiert ist. Die Patch-ID ist ACSD-50345. Beachten Sie, dass das Problem teilweise in Adobe Commerce 2.4.6 behoben wurde und in Adobe Commerce 2.4.7 vollständig behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.5-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

**1. Fall**

Google reCAPTCHA v2 wird nach Übermittlung einer fehlgeschlagenen Zahlung nicht neu geladen.

<u>Zu reproduzierende Schritte</u>

1. Konfigurieren **[!UICONTROL Google reCAPTCHA v2]** (*Ich bin kein Roboter*).
1. Aktivieren Sie die **[!UICONTROL reCAPTCHA]** zum Checkout.
1. Versuchen Sie, eine Bestellung aufzugeben, ohne auf **[!UICONTROL reCAPTCHA]**.
1. Sobald der Benutzer die Fehlermeldung für die fehlende reCAPTCHA erhält (*reCAPTCHA-Validierung fehlgeschlagen, versuchen Sie es erneut.*), klicken Sie auf die **[!UICONTROL reCAPTCHA]** und versuchen Sie dann, eine Bestellung aufzugeben.

<u>Erwartete Ergebnisse</u>

Die Bestellung wird nicht mit einem falschen reCAPTCHA platziert.

<u>Tatsächliche Ergebnisse</u>

Ein Fehler wird ausgegeben - *reCAPTCHA-Validierung fehlgeschlagen, versuchen Sie es erneut.* und *Kein Warenkorb mit ID = 4*

**Fall 2**

Google reCAPTCHA v3 Invisible funktioniert beim Checkout nicht und die Bestellung kann nicht platziert werden. `PlaceOrder` -Ereignis nicht ausgelöst wird.

<u>Zu reproduzierende Schritte</u>

1. Konfigurieren Sie die **[!UICONTROL reCAPTCHA v3 Invisible]** aus dem **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Security]**.
1. Aktivieren **[!UICONTROL reCAPTCHA v3 Invisible]** zum Auschecken/Platzieren einer Bestellung unter der **[!UICONTROL Storefront]** Registerkarte.
1. Versuchen Sie, eine Bestellung bei der [!UICONTROL Check/Money order] Zahlungsmethode.

<u>Erwartete Ergebnisse</u>

Die Bestellung sollte bei der **[!UICONTROL reCAPTCHA]** aktiviert.

<u>Tatsächliche Ergebnisse</u>

Nachdem Sie auf **[!UICONTROL Place Order]** -Schaltfläche, wird sie deaktiviert und nichts passiert weiter.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
