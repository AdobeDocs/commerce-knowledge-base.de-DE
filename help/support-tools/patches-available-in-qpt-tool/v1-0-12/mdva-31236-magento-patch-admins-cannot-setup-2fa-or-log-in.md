---
title: "MDVA-31236: Administratoren können 2FA nicht einrichten oder sich anmelden"
description: Der Patch MDVA-31236 behebt das Problem, dass die Commerce-Admin-Benutzer mit benutzerdefiniertem Ressourcenzugriff keine [Zweifaktorauthentifizierung (2FA)](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html) einrichten oder sich anmelden können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 installiert ist.
exl-id: b75d7a19-3c17-4389-b359-7aeeb8797539
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# MDVA-31236: Administratoren können 2FA nicht einrichten oder sich anmelden

Der Patch MDVA-31236 behebt das Problem, dass die Commerce-Admin-Benutzer mit benutzerdefiniertem Ressourcenzugriff keine [Zweifaktorauthentifizierung (2FA)](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html) einrichten oder sich anmelden können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 installiert ist.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce in der Cloud-Infrastruktur 2.4.0.

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce On-Premise und Adobe Commerce in der Cloud-Infrastruktur 2.4.0-2.4.1.

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Benutzer ohne Administratorberechtigungen können derzeit ihren persönlichen 2FA-Zugriff nicht einrichten. 2FA, wie in Adobe Commerce implementiert, enthält zwei ACL-Rollen. Eine Rolle wirkt sich auf die globale Systemkonfiguration aus und ist nur bei der Konfiguration des Systems erforderlich. Die zweite ACL-Rolle wirkt sich auf einzelne 2FA-Benutzerkonten aus. Ein Administrator muss diesen zweiten Typ von 2FA ACL konfigurieren.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) verfügbare Patches.
