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

Der Patch MDVA-36464 behebt das Problem, dass die Einstellungen für den Versand von E-Mails auf Store-Ansichtsebene nicht funktionieren. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 installiert ist. Die Patch-ID lautet MDVA-36464. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.4.0-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Voraussetzung:</u>

Installieren Sie clean Adobe Commerce.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine zusätzliche Website-, Store- und Store-Ansicht (in diesem Beispiel ist die zweite Website *website2*).
1. Deaktivieren **Email notification** auf globaler Ebene in **Store** > **Konfiguration** > **Erweitert** > **System** > **E-Mail-Sendeeinstellungen**.
1. Aktivieren **Email notification** auf *website2* level (**E-Mail-Kommunikation deaktivieren** = *Nein*).
1. Erstellen Sie in Admin einen neuen Benutzer und weisen Sie ihn dem *website2*.
1. Klicken Sie in Admin auf der Seite zur Kundenbearbeitung auf **Kennwort zurücksetzen** für den oben in Schritt 4 erstellten Kunden.

<u>Erwartete Ergebnisse</u>:

Beide **Willkommens-E-Mail** und **Passwort-E-Mail zurücksetzen** werden wie erwartet gesendet, da **E-Mail-Kommunikation deaktivieren** = *Nein* für die zweite Website (Beispiel: *website2*).

<u>Tatsächliche Ergebnisse</u>:

* Die **Willkommens-E-Mail** nachdem die Erstellung des neuen Kunden nicht ausgelöst wurde.
* Die **Passwort-E-Mail zurücksetzen** nicht ausgelöst wird.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
