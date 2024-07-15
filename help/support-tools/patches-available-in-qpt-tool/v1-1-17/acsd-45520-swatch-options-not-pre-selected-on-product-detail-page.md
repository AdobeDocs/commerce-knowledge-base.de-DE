---
title: "ACSD-45520: Musteroptionen nicht auf der Produktdetailseite ausgewählt"
description: Der Patch ACSD-45520 behebt das Problem, dass Musteroptionen nicht auf der Produktdetailseite vorausgewählt sind, wenn ein Benutzer konfigurierbare Produkte aus dem Warenkorb bearbeitet. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 installiert ist. Die Patch-ID ist ACSD-45520. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.
exl-id: 941f4a45-bc3c-44c0-a582-ddfe179fa8c3
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-45520: Auf der Produktdetailseite nicht ausgewählte Musteroptionen

Der Patch ACSD-45520 behebt das Problem, dass Musteroptionen nicht auf der Produktdetailseite vorausgewählt sind, wenn ein Benutzer konfigurierbare Produkte aus dem Warenkorb bearbeitet. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 installiert ist. Die Patch-ID ist ACSD-45520. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Musteroptionen werden nicht auf der Produktdetailseite ausgewählt, wenn ein Benutzer konfigurierbare Produkte aus dem Warenkorb bearbeitet.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein konfigurierbares Produkt mit Produktoptionen (z. B. Farbe).
1. Fügen Sie das konfigurierbare Produkt zum Warenkorb hinzu.
1. Gehen Sie zur Seite Mein Warenkorb .
1. Klicken Sie auf die Schaltfläche &quot;Bearbeiten&quot;im konfigurierbaren Produkt, das in Schritt 1 hinzugefügt wurde.
1. Beachten Sie die Produktoptionen auf der Bearbeitungsseite.

<u>Erwartete Ergebnisse</u>:

Die Produktoptionen sind ausgewählt.

<u>Tatsächliche Ergebnisse</u>:

Produktoptionen sind nicht ausgewählt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
