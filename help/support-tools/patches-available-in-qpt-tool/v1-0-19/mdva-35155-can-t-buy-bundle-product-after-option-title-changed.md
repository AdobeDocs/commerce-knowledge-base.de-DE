---
title: "MDVA-35155: Kann kein Bundle-Produkt kaufen, nachdem der Optionstitel geändert wurde."
description: Der MDVA-35155-Patch behebt das Problem, dass ein Bundle-Produkt nicht gekauft werden kann, nachdem der Optionstitel geändert wurde. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 installiert ist. Die Patch-ID lautet MDVA-35155. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben wurde.
exl-id: 79770c69-1bb0-48d8-acdf-c8c1272f9da8
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-35155: Bundle-Produkt nach Änderung des Optionstitels nicht kaufen

Der MDVA-35155-Patch behebt das Problem, dass ein Bundle-Produkt nicht gekauft werden kann, nachdem der Optionstitel geändert wurde. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 installiert ist. Die Patch-ID lautet MDVA-35155. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce in Cloud-Infrastruktur 2.3.5

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce vor Ort und Adobe Commerce über Cloud-Infrastruktur 2.3.0-2.3.5-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Bundle-Produkte können nicht gekauft werden, nachdem der Optionstitel geändert wurde.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein neues Bundle-Produkt über den **Produktimport**.
1. Das Produkt ist sowohl im Admin- als auch im Frontend normal (auf Lager und kann zum Warenkorb hinzugefügt werden).
1. Aktualisieren Sie dasselbe Produkt mit Namensänderungen in `bundle_values` und importieren Sie das Produkt erneut.

<u>Erwartete Ergebnisse</u>:

Die vorhandene Bundle-Option wird auf den neuen Namen aktualisiert und behält die gleichen Elemente bei.

<u>Tatsächliche Ergebnisse</u>:

* Der Administrator versucht, Produkte mit derselben SKU in einem Abschnitt mit einer einzelnen Bundle-Option zusammenzuführen, was zu einem leeren Optionsabschnitt führt.
* Das Produkt ist nicht vorrätig (selbst nach einer Neuindizierung).

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) verfügbare Patches.
