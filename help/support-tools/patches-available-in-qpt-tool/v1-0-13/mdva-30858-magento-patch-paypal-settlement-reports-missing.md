---
title: "MDVA-30858: PayPal Settlement reports missing"
description: "Der Patch MDVA-30858 behebt fehlende PayPal-Vergleichsberichte bei mehreren PayPal-Konten. Die Berichte sollten unter Admin-Seitenleiste &gt; **Reports** &gt; Sales&gt; **PayPal-Vergleich** verfügbar sein. Stattdessen wird die Nachricht angezeigt: *Wir konnten keine Datensätze finden.* angezeigt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde."
exl-id: 268aa74c-5cb5-4653-a6c9-1d4c30167e6a
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# MDVA-30858: PayPal-Vergleichsberichte fehlen

Der Patch MDVA-30858 behebt fehlende PayPal-Vergleichsberichte bei mehreren PayPal-Konten. Die Berichte sollten unter Admin-Seitenleiste > **Berichte** > Verkauf > **PayPal-Vergleich** verfügbar sein. Stattdessen wird die Meldung *Wir konnten keine Datensätze finden.* angezeigt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce in Cloud-Infrastruktur 2.3.4

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Behebung des Problems, bei dem keine Datensätze in **Berichten** > Vertrieb > **PayPal-Vergleich** gefunden wurden, wenn mehrere PayPal-Konten vorhanden waren.

<u>Zu reproduzierende Schritte</u>:

1. PayPal-Vergleichsberichte konfigurieren.
1. Wechseln Sie zu Admin, zu **Berichte** > Vertrieb > **PayPal-Vergleich**.
1. Klicken Sie für die neuesten Updates oben rechts auf **Aktualisierungen abrufen** .

<u>Erwartete Ergebnisse</u>:

Berichte sollten angezeigt werden.

<u>Tatsächliche Ergebnisse</u>:

Im Raster wird nichts angezeigt, obwohl Berichte verfügbar sind.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
