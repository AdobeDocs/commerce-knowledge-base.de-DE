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

Der Patch MDVA-35910 behebt das Problem, bei dem die Formularüberprüfung für Kundenkonto erstellen fehlschlägt, wenn die **Als Kunde anmelden** -Erweiterung deaktiviert ist. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 ist installiert. Die Patch-ID lautet MDVA-35910. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce in Cloud-Infrastruktur 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1-2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **Stores > Konfiguration > Kunden**. Deaktivieren **Als Kunde anmelden** im Admin.
1. under **Als Kunde anmelden**, set **Erweiterung aktivieren** = *Nein*.
1. Speichern Sie die Konfiguration und leeren Sie den Cache.
1. Navigieren Sie zurück zur Storefront und klicken Sie auf **registrieren** (Erstellen Sie ein Kundenkonto).
1. Füllen Sie das Kontoformular aus und bestätigen Sie, ob die Validierung unter **E-Mail bestätigen** funktioniert oder nicht.

<u>Erwartete Ergebnisse</u>:

Der Prozess zur Erstellung des Kundenkontos wird ohne Fehler abgeschlossen.

<u>Tatsächliche Ergebnisse</u>:

Der Erstellungsprozess für Kundenkonten wird nicht abgeschlossen und stattdessen werden Fehler in der JavaScript-Konsole angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
