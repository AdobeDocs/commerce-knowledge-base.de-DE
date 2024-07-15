---
title: "MDVA-23845: E-Mail-Vorlage kann nicht in der Vorschau angezeigt werden, wenn die JS-Minimierung aktiviert ist"
description: Der Magento-Patch MDVA-23845 behebt das Problem, dass die E-Mail-Vorlage in Admin nicht in der Vorschau angezeigt werden kann, wenn die JS-Minimierung aktiviert ist.
exl-id: 08579251-a0aa-4e84-9d6a-3fa2999d9c05
feature: Communications, Marketing Tools
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# MDVA-23845: E-Mail-Vorlage kann nicht in der Vorschau angezeigt werden, wenn die JS-Minimierung aktiviert ist

Der Magento-Patch MDVA-23845 behebt das Problem, dass die E-Mail-Vorlage in Admin nicht in der Vorschau angezeigt werden kann, wenn die JS-Minimierung aktiviert ist.

Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 installiert ist. Die Patch-ID lautet MDVA-23845. Bitte beachten Sie, dass das Problem in Magento Version 2.3.5 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Magento-Version erstellt:** Magento Commerce Cloud 2.3.3

**Kompatibel mit Magento-Versionen:** Magento Commerce und Magneto Commerce Cloud 2.3.2-2.3.4-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u> :

1. Aktivieren Sie **JS minification** in **Admin > Stores > Konfiguration > JavaScript-Einstellungen > Minify JavaScript Files** = *Ja* .
1. Wechseln Sie Magento in den Produktionsmodus.
1. Gehen Sie zu **Admin > Marketing > Kommunikation > E-Mail-Vorlagen** .
1. Klicken Sie auf **Neue Vorlage hinzufügen** .
1. Wählen Sie die Vorlage **Neue Bestellung** aus.
1. Klicken Sie auf die Schaltfläche **Vorlage laden** .
1. Füllen Sie **Vorlagenname** mit **Neuer Auftrag** aus.
1. Klicken Sie auf die Schaltfläche **Vorlage speichern** .
1. Klicken Sie im Raster E-Mail-Vorlagen in der Spalte **Aktionen** auf den Link **Vorschau** .

<u>Erwartete Ergebnisse</u> :

Die E-Mail-Vorlagenvorschau wird wie erwartet im geöffneten Popup-Fenster angezeigt.

<u>Tatsächliche Ergebnisse</u> :

Die E-Mail-Vorlagenvorschau wird nicht im geöffneten Popup-Fenster angezeigt. Das Popup-Fenster ist leer, und es können JS-Fehler auftreten.

## Wenden Sie den Patch an

Um einzelne Patches anzuwenden, verwenden Sie je nach Magento-Produkt die folgenden Links:

* Magento Commerce: DevDocs [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html) .
* Magento Commerce Cloud: DevDocs [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) .

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) .
* [Überprüfen Sie den Patch auf ein Magento-Problem mit dem Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) .

Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
