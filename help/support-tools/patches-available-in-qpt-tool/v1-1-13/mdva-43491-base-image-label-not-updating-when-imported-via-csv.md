---
title: "MDVA-43491: Grundlegende Bildbeschriftung wird beim Import über CSV nicht aktualisiert."
description: Der Patch MDVA-43491 behebt das Problem, dass das "base_image_label"nicht aktualisiert wird, wenn es über eine CSV-Datei für eine Website mit mehreren Stores importiert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-43491. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: d744423a-f582-4410-8d66-861229cce1b5
feature: Data Import/Export
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# MDVA-43491: Grundlegende Bildbeschriftung wird beim Import über CSV nicht aktualisiert

Der Patch MDVA-43491 behebt das Problem, dass der `base_image_label` nicht aktualisiert wird, wenn er über eine CSV-Datei für eine Multi-Store-Website importiert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-43491. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der `base_image_label` wird nicht aktualisiert, wenn er mit einer CSV-Datei für eine Website mit mehreren Stores importiert wird.

<u>Voraussetzungen</u>:

Eine oder mehrere vorhandene nicht standardmäßige Websites, Stores und Store-Ansichten.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein neues Produkt.

   * Laden Sie ein Bild hoch.
   * Weisen Sie das Produkt den neu erstellten Websites zu.

1. Exportieren Sie das Produkt als CSV.
1. Aktualisieren Sie die `base_image_label` für jede Store-Ansicht, indem Sie die Standardzeile der CSV-Datei duplizieren.
1. Importieren Sie die CSV-Datei. Dadurch werden die Beschriftungen für jeden Store korrekt aktualisiert, was auf der Seite zur Produktbearbeitung auf der Registerkarte **Bilder und Videos** überprüft werden kann.
1. Exportieren Sie die CSV-Datei erneut und aktualisieren Sie die Spalte `base_image_label` mit unterschiedlichen Werten.
1. Importieren Sie die CSV-Datei erneut.
1. Öffnen Sie das Produkt in der Admin-Konsole und überprüfen Sie, ob die Bezeichnung für jede Store-Ansicht aktualisiert wurde.

<u>Erwartete Ergebnisse</u>:

Alternativtext (Bildbezeichnung) wird mit dem speicherspezifischen Wert gemäß der CSV-Datei aktualisiert.

<u>Tatsächliche Ergebnisse</u>:

Alternativtext (Bildbezeichnung) wird nicht mit dem Wert `base_image_label` in der CSV-Datei aktualisiert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
