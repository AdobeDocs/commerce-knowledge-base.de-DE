---
title: "MDVA-38346: Datumsfilter, die nicht funktionieren, wenn sich die Adobe Commerce-Zeitzone von der lokalen unterscheidet"
description: Der Patch MDVA-38346 behebt das Problem, bei dem Datumsfilter nicht ordnungsgemäß funktionieren, wenn die Adobe Commerce-Zeitzone sich von der lokalen Zeitzone der Umgebung unterscheidet. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-38346. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: 221ac249-add3-46e9-b0da-688eacdb753e
feature: Configuration
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-38346: Datumsfilter, die nicht funktionieren, wenn sich die Adobe Commerce-Zeitzone von der lokalen unterscheidet

Der Patch MDVA-38346 behebt das Problem, bei dem Datumsfilter nicht ordnungsgemäß funktionieren, wenn die Adobe Commerce-Zeitzone sich von der lokalen Zeitzone der Umgebung unterscheidet. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-38346. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1, 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Datumsfilter funktionieren nicht ordnungsgemäß, wenn sich die Zeitzone von Adobe Commerce von der Zeitzone der lokalen Umgebung unterscheidet.

<u>Zu reproduzierende Schritte</u>:

1. Ändern Sie die Zeitzone in Australien/Sydney.
1. Legen Sie einige Bestellungen auf.
1. Erstellen Sie für sie Rechnungen.
1. Wechseln Sie zu **Verkauf** > **Rechnungen** und filtern Sie nach Rechnungsdatum (aktuelles Datum - aktuelles Datum).
1. Datum überprüfen.

<u>Erwartete Ergebnisse</u>:

Das angezeigte Rechnungsdatum und der tatsächliche Filter stimmen überein.

<u>Tatsächliche Ergebnisse</u>:

Das angezeigte Rechnungsdatum liegt einem Tag vor dem tatsächlichen Filter (aktuelles Datum + 1 Tag).

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
