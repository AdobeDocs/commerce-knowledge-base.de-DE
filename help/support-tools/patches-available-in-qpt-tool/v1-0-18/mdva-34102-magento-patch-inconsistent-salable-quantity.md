---
title: "MDVA-34102: Inkonsistente Verkaufsmenge"
description: Der Patch MDVA-34102 behebt das Problem, dass die Standardvorräte für deaktivierte Produkte auf den Seiten "Produktraster"und "Produkt bearbeiten"in Admin bei null liegen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 installiert ist. Die Patch-ID lautet MDVA-34102. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.3 behoben werden soll.
exl-id: cb1d4689-c122-4afd-8597-b2627027aaf3
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-34102: Inkonsistente Verkaufsmenge

Der Patch MDVA-34102 behebt das Problem, dass die Standardvorräte für deaktivierte Produkte auf den Seiten &quot;Produktraster&quot;und &quot;Produkt bearbeiten&quot;in Admin bei null liegen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 installiert ist. Die Patch-ID lautet MDVA-34102. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.3 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.3.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce vor Ort und Adobe Commerce über Cloud-Infrastruktur 2.3.0-2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Richten Sie zwei Websites mit Geschäften und Store-Ansichten ein.
1. Erstellen Sie eine zusätzliche Quelle und ein weiteres Lager.
1. Fügen Sie ein einfaches Produkt hinzu:
   * Legen Sie **Produkt aktivieren** = *Nein* fest.
   * Weisen Sie zwei Quellen mit dem Wert **Source-Elementstatus** = *Auf Lager* eine Menge zu, die größer als null ist (Beispiel: **Standardbestand** = *123* und **UK-Lager** = *123*).
1. Speichern Sie das Produkt.
1. Überprüfen Sie die Registerkarte **Produktverkaufsmenge**.

<u>Erwartete Ergebnisse</u>:

Sowohl der Standardbestand als auch der britische Bestand = *123.*

Die Standardlagermenge wird für deaktivierte Produkte auf den Seiten &quot;Produktraster&quot;und &quot;Produkt bearbeiten&quot;in der Admin-Konsole korrekt angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Der Standardbestand = *0* und der britische Bestand = *123.*

Die standardmäßige Lagermenge für deaktivierte Produkte auf den Seiten &quot;Produktraster&quot;und &quot;Produkt bearbeiten&quot;in der Admin-Konsole ist null.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) verfügbare Patches.
