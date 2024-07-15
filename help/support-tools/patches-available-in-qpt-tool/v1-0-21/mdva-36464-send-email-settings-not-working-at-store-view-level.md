---
title: "MDVA-36464: E-Mail-Einstellungen senden, die auf Store-Ansichtsebene nicht funktionieren"
description: Der Patch MDVA-36464 behebt das Problem, dass die Einstellungen für den Versand von E-Mails auf Store-Ansichtsebene nicht funktionieren. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 installiert ist. Die Patch-ID lautet MDVA-36464. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.
exl-id: cdf7e208-90ee-4711-8407-026da42fe3c8
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-36464: E-Mail-Einstellungen senden, die auf Store-Ansichtsebene nicht funktionieren

Der Patch MDVA-36464 behebt das Problem, dass die Einstellungen für den Versand von E-Mails auf Store-Ansichtsebene nicht funktionieren. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 installiert ist. Die Patch-ID lautet MDVA-36464. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.4.0-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Voraussetzung:</u>

Installieren Sie clean Adobe Commerce.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine zusätzliche Website-, Store- und Store-Ansicht (in diesem Beispiel ist die zweite Website *website2*).
1. Deaktivieren Sie **E-Mail-Benachrichtigung** auf globaler Ebene in **Store** > **Konfiguration** > **Erweitert** > **System** > **E-Mail-Sendeeinstellungen**.
1. Aktivieren Sie **E-Mail-Benachrichtigung** auf der Ebene *Website2* (**E-Mail-Kommunikation deaktivieren** = *Nein*).
1. Erstellen Sie in Admin einen neuen Benutzer und weisen Sie ihn der *Website2* zu.
1. Klicken Sie in Admin auf der Seite zur Kundenbearbeitung für den oben in Schritt 4 erstellten Kunden auf **Kennwort zurücksetzen** .

<u>Erwartete Ergebnisse</u>:

Sowohl die **Begrüßungs-E-Mail** als auch die **Kennwort-E-Mail zurücksetzen** werden erwartungsgemäß gesendet, da **E-Mail-Kommunikation deaktivieren** = *Nein* für die zweite Website (Beispiel: *Website2*).

<u>Tatsächliche Ergebnisse</u>:

* Die **Begrüßungs-E-Mail** nach der Erstellung des neuen Kunden wird nicht ausgelöst.
* Die **Kennwort-E-Mail zurücksetzen** wird nicht ausgelöst.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
