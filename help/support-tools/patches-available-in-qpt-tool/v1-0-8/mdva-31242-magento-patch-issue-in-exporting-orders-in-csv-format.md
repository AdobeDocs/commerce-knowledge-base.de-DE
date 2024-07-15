---
title: "MDVA-31242: Ausgabe bei Exportaufträgen im CSV-Format"
description: Der Patch MDVA-31242 behebt das Problem, dass beim Export von Bestellungen im CSV-Dateiformat ein Fehler auftritt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.
exl-id: 1e343f23-5b10-492b-885f-8113ace4777f
feature: B2B, Data Import/Export, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# MDVA-31242: Ausgabe in CSV-Exportbestellungen

Der Patch MDVA-31242 behebt das Problem, dass beim Export von Bestellungen im CSV-Dateiformat ein Fehler auftritt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce auf Cloud-Infrastruktur 2.4.0

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (Bereitstellungsmethoden) 2.3.0 - 2.4.0-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich beim Admin-Backend an.
1. Aktivieren Sie **Firma** unter **Geschäfte** > **Konfiguration** > **B2B-Funktionen**.
1. Wechseln Sie zu **Verkauf** > **Bestellungen**.
1. Klicken Sie auf das Kontrollkästchen **Spalte** > **Firmenname** .
1. Geben Sie einen beliebigen Wert in das Textfeld **Filter** > **Firmenname** ein.
1. Klicken Sie auf die Schaltfläche **Filter anwenden** .
1. Klicken Sie auf die Schaltfläche **Exportieren** > **CSV** > **Exportieren** .

<u>Erwartete Ergebnisse</u>:

Das Popup für die ausgewählte Datei wird wie erwartet geöffnet.

<u>Tatsächliche Ergebnisse</u>:

Weißer Bildschirm mit dem Fehler *Es wurde ein Fehler bei der Verarbeitung Ihrer Anfrage* angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
