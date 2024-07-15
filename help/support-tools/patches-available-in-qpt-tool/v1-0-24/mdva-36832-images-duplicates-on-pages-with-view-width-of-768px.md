---
title: "MDVA-36832: Bilder duplizieren auf Seiten mit 768 px Ansichtsbreite"
description: Der Patch MDVA-36832 behebt das Problem, dass Bilder auf Seiten mit einer Ansichtsbreite von 768 Pixel dupliziert werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24 installiert ist. Die Patch-ID lautet MDVA-36832. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: 3eb0c11b-d93a-4676-afd1-8f6592c6cd6d
feature: Configuration, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# MDVA-36832: Bilder duplizieren auf Seiten mit 768 px Ansichtsbreite

Der Patch MDVA-36832 behebt das Problem, dass Bilder auf Seiten mit einer Ansichtsbreite von 768 Pixel dupliziert werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24 installiert ist. Die Patch-ID lautet MDVA-36832. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce für die Cloud-Infrastruktur 2.3.5-p2

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce On-Premise und Adobe Commerce in der Cloud-Infrastruktur 2.3.4 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Bilder werden auf Seiten mit einer Ansichtsbreite von 768 Pixel dupliziert.

<u>Zu reproduzierende Schritte:</u>

1. Gehen Sie zu Backend > INHALT > Seiten und bearbeiten Sie eine beliebige Seite.
1. Fügen Sie ein beliebiges Bild zur Seite hinzu.
1. Öffnen Sie die bearbeitete Seite im Frontend.
1. Öffnen Sie Entwicklertools in Chrome.
1. Aktivieren Sie &quot;Geräteansicht&quot;und wählen Sie &quot;iPad-Ansicht&quot;oder legen Sie die Seitenbreite auf 768 px fest.

<u>Tatsächliches Ergebnis:</u>

Das Bild wird dupliziert.

<u>Erwartetes Ergebnis:</u>

Nur ein hinzugefügtes Bild sollte auf der Seite sichtbar sein.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
