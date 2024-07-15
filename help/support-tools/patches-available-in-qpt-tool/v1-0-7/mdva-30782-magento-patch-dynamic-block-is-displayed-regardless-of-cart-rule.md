---
title: "MDVA-30782: Dynamischer Block wird unabhängig von der Warenkorbregel angezeigt."
description: Der Patch MDVA-30782 behebt das Problem, dass ein dynamischer Block unabhängig von der Warenkorbregel angezeigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.
exl-id: 88da8853-aae7-4fd9-82ba-a4e9fc99cf53
feature: Cache, Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-30782: Dynamischer Block wird unabhängig von der Warenkorbregel angezeigt

Der Patch MDVA-30782 behebt das Problem, dass ein dynamischer Block unabhängig von der Warenkorbregel angezeigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.3.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5 - 2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der dynamische Block wird auch dann auf der Seite angezeigt, wenn die zugehörige Bedingung der Katalogpreisregel nicht erfüllt ist.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie zwei Produkte.
1. Erstellen Sie eine Katalogpreisregel, die nur für eines dieser Produkte gilt.
1. Erstellen Sie einen dynamischen Block und weisen Sie ihm die neu erstellte Katalogpreisregel zu.
1. Erstellen Sie ein Widget mit den folgenden Parametern:
   * Typ = dynamische Blockdrehung
   * Dynamische Bausteine, die angezeigt werden sollen = bestimmte dynamische Bausteine
   * Dynamische Blöcke angeben = Formularblock-Schritt \#3Layout-Aktualisierungen (es kann beliebig sein)
   * Anzeigen unter = Alle Produktarten
   * Container = Produkthilfeinformationen
1. Führen Sie eine Neuindizierung durch und leeren Sie den Cache.
1. Überprüfen Sie beide Produktseiten für den Schritt &quot;Dynamischer Baustein - Formular&quot;\#3.

<u>Erwartete Ergebnisse</u>:

Der dynamische Block wird nur auf der ersten Produktseite angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Der dynamische Block wird auf beiden Produktseiten angezeigt. Bei dynamischen Bausteinen, die angezeigt werden sollen = Katalogpreisregel Bezieht sich auf Schritt \#3, ist das Ergebnis dasselbe.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
