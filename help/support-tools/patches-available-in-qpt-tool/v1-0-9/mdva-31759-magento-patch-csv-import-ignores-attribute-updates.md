---
title: 'MDVA-31759 Patch: CSV-Import ignoriert Attributaktualisierungen'
description: Der Patch MDVA-31759 behebt das Problem, dass beim CSV-Import zusätzliche Attribute mit den Typen *Dropdown* und *Textbereich* ignoriert werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.
exl-id: 5426866c-893f-4abe-bfbc-6e7b30dd8dab
feature: Attributes, Data Import/Export
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-31759 Patch: CSV-Import ignoriert Attributaktualisierungen

Der Patch MDVA-31759 behebt das Problem, dass beim CSV-Import zusätzliche Attribute mit den Typen *Dropdown* und *Textbereich* ignoriert werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.4.0

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.3.0 - 2.4.1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Beim CSV-Import werden zusätzliche Attribute mit den Typen *Dropdown* und *Textbereich* ignoriert.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei Commerce Admin an.
1. Erstellen Sie ein Produktattribut mit der folgenden Konfiguration:
   * **Standardbezeichnung**: *G003*
   * **Katalogeingabetyp für Store Owner**: *Textbereich* oder *Dropdown*
   * **Attributcode**: *G003*
   * **Umfang**: *Global*
1. Fügen Sie das oben genannte Attribut zum standardmäßigen Attributsatz hinzu.
1. Erstellen Sie ein Produkt mit dem standardmäßigen Attributsatz und geben Sie einen Wert für das neue Attribut an.
1. Exportieren Sie das Produkt in CSV.
1. Aktualisieren Sie den Attributwert in der Spalte **additional\_attributes** .
1. Importieren Sie die aktualisierte CSV.

<u>Erwartete Ergebnisse</u>:

Der Attributwert G003 wird aktualisiert.

<u>Tatsächliche Ergebnisse</u>:

Der Attributwert G003 wird nicht aktualisiert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie in der [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
