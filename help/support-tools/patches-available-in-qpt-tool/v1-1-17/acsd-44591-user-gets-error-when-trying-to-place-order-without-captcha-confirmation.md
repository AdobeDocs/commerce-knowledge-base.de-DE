---
title: "ACSD-44591: Fehler bei Bestellung ohne CAPTCHA-Bestätigung"
description: Der Patch ACSD-44591 behebt das Problem, bei dem der Benutzer beim Versuch, eine Bestellung ohne CAPTCHA-Bestätigung zu tätigen, Fehler erhält.
exl-id: 5459aa14-dcba-474d-aafa-e4cc73daafbc
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-44591: Fehler bei Bestellung ohne CAPTCHA-Bestätigung

Der Patch ACSD-44591 behebt das Problem, bei dem der Benutzer beim Versuch, eine Bestellung ohne CAPTCHA-Bestätigung zu tätigen, Fehler erhält.
Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 installiert ist. Die Patch-ID lautet ACSD-44591. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Benutzer erhält beim Versuch, eine Bestellung ohne CAPTCHA-Bestätigung zu tätigen, Fehler.

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren Sie Google ReCaptcha v2 (ich bin kein Roboter).
1. Aktivieren Sie ReCaptcha für den Checkout.
1. Versuchen Sie, eine Bestellung zu tätigen, ohne auf das ReCaptcha zu klicken.
1. Sobald Sie die Fehlermeldung für fehlende ReCaptcha (*ReCaptcha-Validierung fehlgeschlagen, versuchen Sie es erneut*), klicken Sie auf **ReCaptcha** und versuchen Sie dann, eine Bestellung aufzugeben.

<u>Erwartete Ergebnisse</u>:

Die Bestellung wird nicht mit falschem ReCaptcha platziert.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten die folgenden Fehler:

* *Erneutes Captcha-Validierung fehlgeschlagen, versuchen Sie es erneut*
* *Kein solcher Warenkorb mit ID = 1*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
