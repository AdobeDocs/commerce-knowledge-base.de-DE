---
title: '"MDVA-35910: Formularüberprüfung unterbrochen, wenn "Als Kunde anmelden"deaktiviert ist'
description: Der Patch MDVA-35910 behebt das Problem, dass die Formularüberprüfung für das Erstellen eines Kundenkontos fehlschlägt, wenn die Erweiterung **Als Kunde anmelden** deaktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 installiert ist. Die Patch-ID lautet MDVA-35910. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben wurde.
exl-id: fa63d725-33f0-4422-bcd5-d62dfee01b65
feature: Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-35910: Formularüberprüfung unterbrochen, wenn &quot;Als Kunde anmelden&quot;deaktiviert ist

Der Patch MDVA-35910 behebt das Problem, bei dem die Formularüberprüfung zum Erstellen eines Kundenkontos fehlschlägt, wenn die Erweiterung **Als Kunde anmelden** deaktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 installiert ist. Die Patch-ID lautet MDVA-35910. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce in Cloud-Infrastruktur 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1-2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **Stores > Konfiguration > Kunden**. Deaktivieren Sie **Als Kunde anmelden** im Admin.
1. Legen Sie unter **Als Kunde anmelden** **Erweiterung aktivieren** = *Nein* fest.
1. Speichern Sie die Konfiguration und leeren Sie den Cache.
1. Navigieren Sie zurück zur Storefront und klicken Sie auf **Registrieren** (Kundenkonto erstellen).
1. Füllen Sie das Kontoformular aus und überprüfen Sie, ob die Validierung unter **E-Mail bestätigen** funktioniert oder nicht.

<u>Erwartete Ergebnisse</u>:

Der Prozess zur Erstellung des Kundenkontos wird ohne Fehler abgeschlossen.

<u>Tatsächliche Ergebnisse</u>:

Der Erstellungsprozess für Kundenkonten wird nicht abgeschlossen und stattdessen werden Fehler in der JavaScript-Konsole angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
