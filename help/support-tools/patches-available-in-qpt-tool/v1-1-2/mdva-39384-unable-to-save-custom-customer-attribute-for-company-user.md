---
title: "MDVA-39384: Benutzerdefiniertes Kundenattribut für Unternehmensbenutzer kann nicht gespeichert werden"
description: Der Patch MDVA-39384 behebt das Problem, dass das benutzerdefinierte Kundenattribut für einen Unternehmensbenutzer nicht gespeichert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-39384. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: b9864ca6-307b-4649-b764-4512abc503d3
feature: Attributes, B2B, Companies
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# MDVA-39384: Benutzerdefiniertes Kundenattribut für Unternehmensbenutzer kann nicht gespeichert werden

Der Patch MDVA-39384 behebt das Problem, dass das benutzerdefinierte Kundenattribut für einen Unternehmensbenutzer nicht gespeichert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-39384. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.1 - 2.3.6, 2.4.1 - 2.4.3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Benutzerdefiniertes Kundenattribut für einen Unternehmensbenutzer wird nicht gespeichert.

<u>Voraussetzungen</u>:

B2B-Module sind installiert.

<u>Zu reproduzierende Schritte</u>:

1. Wechseln Sie zu **Stores** > Einstellungen > **Konfiguration** > **B2B-Funktionen** und legen Sie die Option **Unternehmen aktivieren** auf &quot;Ja&quot;fest.
1. Erstellen Sie ein benutzerdefiniertes Kundenattribut:
   * Erforderliche Werte: Ja (optional, aktivieren Sie sie, damit der Validierungsfehler angezeigt wird).
   * In Storefront anzeigen: Ja.
   * Forms zur Verwendung in: Alle in der Liste verfügbar.
1. Erstellen Sie ein Unternehmen und melden Sie sich als Unternehmensadministrator an.
1. Navigieren Sie in Ihrem Konto zu Unternehmensstruktur .
1. Klicken Sie auf den Link **Benutzer hinzufügen** .
1. Füllen Sie das Formular einschließlich des benutzerdefinierten Attributs aus.
1. Klicken Sie auf **Speichern**.

<u>Erwartete Ergebnisse</u>:

Die benutzerdefinierten Attributwerte werden beim neuen Unternehmensbenutzer gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Die benutzerdefinierten Attributwerte werden NICHT beim neuen Unternehmensbenutzer gespeichert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
