---
title: "MDVA-37068: Falsche Steuer beim Checkout für virtuelle Produkte"
description: Der Patch MDVA-37068 behebt das Problem, wenn die Checkout-Seite einen falschen Steuersatz für virtuelle Produkte anzeigt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26 installiert ist. Die Patch-ID lautet MDVA-37068. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: ef75b41e-e79d-4947-8b74-87966642f808
feature: Cache, Checkout, Orders, Products, Taxes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-37068: Falsche Steuer beim Checkout für virtuelle Produkte angezeigt

Der Patch MDVA-37068 behebt das Problem, wenn die Checkout-Seite einen falschen Steuersatz für virtuelle Produkte anzeigt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26 installiert ist. Die Patch-ID lautet MDVA-37068. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
Adobe Commerce auf Cloud-Infrastruktur 2.3.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**
Adobe Commerce (alle Bereitstellungsmethoden) 2.3.1-2.4.2-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Auf der Checkout-Seite wird ein falscher Steuersatz angezeigt, wenn der Warenkorb nur virtuelle Produkte enthält.

<u>Voraussetzungen</u>:

1. Erstellen Sie zwei separate Steuersätze und Steuervorschriften für zwei verschiedene Länder, z. B. 10 % und 1 %.
1. Erstellen eines virtuellen Produkts.
1. Führen Sie eine Neuindizierung durch und leeren Sie den Cache.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie einen Kunden.
1. Fügen Sie unterschiedliche Abrechnungs- und Versandadressen hinzu.
1. Fügen Sie dem Warenkorb ein virtuelles Produkt hinzu.
1. Markieren Sie die Seite Warenkorb und Checkout .

<u>Erwartete Ergebnisse</u>:

Die auf der Seite Warenkorb und Checkout angezeigte Steuer ist identisch.

<u>Tatsächliche Ergebnisse</u>:

Die auf der Seite Warenkorb und Checkout angezeigte Steuer ist NICHT die gleiche.

## Wenden Sie den Patch an

Um einzelne Patches anzuwenden, verwenden Sie je nach Bereitstellungsmethode die folgenden Links:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
