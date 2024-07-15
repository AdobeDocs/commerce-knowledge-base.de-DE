---
title: "MDVA-33976 Patch: Bundle Out Of Stock nach Option entfernt"
description: Der Patch MDVA-33976 behebt das Problem, dass ein Bundle-Produkt als "Nicht auf Lager"angezeigt wird, nachdem eine seiner Optionen in Admin entfernt wurde. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT) 1.0.15](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.
exl-id: 2e2bc05b-ad31-4e87-b33e-3526f6a42478
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# MDVA-33976 Patch: Bundle Out Of Stock nach Option entfernt

Der Patch MDVA-33976 behebt das Problem, dass ein Bundle-Produkt als &quot;Nicht auf Lager&quot;angezeigt wird, nachdem eine seiner Optionen in Admin entfernt wurde. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT) 1.0.15](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce in der Cloud-Infrastruktur 2.3.3

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce für Cloud-Infrastruktur und Adobe Commerce On-Premise 2.3.0-2.3.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Öffnen Sie ein Bundle-Produkt in der Commerce Admin.
1. Entfernen Sie eine der Bundle-Produktoptionen.
1. Speichern Sie die Änderungen.
1. Öffnen Sie das Produkt auf der Storefront.

<u>Erwartetes Ergebnis</u>:

Der Status des Produktbestands des Bundles wird entsprechend dem Status des untergeordneten Produktbestands aktualisiert.

<u>Tatsächliches Ergebnis</u>:

Das Bundle-Produkt wird als &quot;Nicht auf Lager&quot;angezeigt, unabhängig vom Status des untergeordneten Produkts.

## Wenden Sie den Patch an

Verwenden Sie je nach Adobe Commerce-Produkt die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
