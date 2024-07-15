---
title: "MDVA-33289 Patch: Javascript in Adresse beim Checkout"
description: Der Patch MDVA-33289 behebt das Problem, dass JavaScript bei Zahlung in der Adresse angezeigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 installiert ist. Die Patch-ID lautet MDVA-33289. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben werden sollte.
exl-id: 247e4f05-7e89-4d37-b3d4-c2cae7595267
feature: Checkout, Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# MDVA-33289 Patch: Javascript in Adresse beim Checkout

Der Patch MDVA-33289 behebt das Problem, dass JavaScript bei Zahlung in der Adresse angezeigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 installiert ist. Die Patch-ID lautet MDVA-33289. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben werden sollte.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce in der Cloud-Infrastruktur 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce für Cloud-Infrastruktur und Adobe Commerce On-Premise 2.4.0 - 2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Beim Auschecken mit aktiviertem Google Tag Manager (GTM) wird im Adressfeld JavaScript angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie GTM. Weitere Informationen finden Sie unter [Google Tag Manager](https://docs.magento.com/user-guide/marketing/google-tag-manager.html) in unserem Benutzerhandbuch.
1. Fügen Sie im Schaufenster einige Produkte zum Warenkorb hinzu.
1. Checken Sie es aus.

<u>Tatsächliches Ergebnis</u>:

Der Adressabschnitt wird aktualisiert, enthält jedoch eine Menge JavaScript-Code-Text.

<u>Erwartetes Ergebnis</u>:

Adresse wird angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie in der [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
