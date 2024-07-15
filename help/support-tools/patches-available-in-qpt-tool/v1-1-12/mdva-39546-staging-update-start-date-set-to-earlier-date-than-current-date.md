---
title: "MDVA-39546: Das Startdatum der Staging-Aktualisierung kann auf ein Datum vor dem aktuellen Datum gesetzt werden"
description: Der Patch MDVA-39546 behebt das Problem, bei dem das Startdatum für das Staging-Update auf ein früheres Datum als das aktuelle Datum gesetzt werden kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-39546. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: a66b5d83-2eba-45a6-9eb9-4ba39ef20e16
feature: Staging
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# MDVA-39546: Das Startdatum der Staging-Aktualisierung kann auf ein Datum vor dem aktuellen Datum gesetzt werden

Der Patch MDVA-39546 behebt das Problem, bei dem das Startdatum für das Staging-Update auf ein früheres Datum als das aktuelle Datum gesetzt werden kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-39546. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Startdatum für das Staging-Update kann auf ein Datum vor dem aktuellen Datum gesetzt werden.

<u>Zu reproduzierende Schritte</u>:

1. Planen Sie ein neues Update für ein Produkt mit einem zukünftigen Startdatum.
1. Bearbeiten Sie die Aktualisierung von &quot;**Inhalt**&quot;> &quot;**Inhaltsstaging**&quot;> &quot;**Dashboard**&quot;, aktualisieren Sie das Startdatum mit einem älteren Datum und speichern Sie die Änderung.
1. Öffnen Sie die obige Aktualisierung erneut.

<u>Erwartete Ergebnisse</u>:

Vorherige Daten werden im Bearbeitungsformular angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Werte im Formular fehlen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
