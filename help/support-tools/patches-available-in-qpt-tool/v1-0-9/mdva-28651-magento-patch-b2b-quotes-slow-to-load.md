---
title: "MDVA-28651: B2B - Anführungszeichen langsam laden"
description: Der Patch MDVA-28651 behebt das Problem, bei dem beim Laden von Anführungszeichen mehrere Leistungsprobleme auftreten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.9 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.2 behoben sein sollte.
exl-id: 2d0bfbba-cdf3-4f9e-a900-ce42909fac8e
feature: B2B, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-28651: B2B - Anführungszeichen langsam laden

Der Patch MDVA-28651 behebt das Problem, bei dem beim Laden von Anführungszeichen mehrere Leistungsprobleme auftreten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.9 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.2 behoben sein sollte.

## Betroffene Produkte und Versionen

* Der Patch wurde für Adobe Commerce in der Cloud-Infrastruktur 2.3.4 entwickelt.
* Der Patch ist auch mit den folgenden Adobe Commerce-Versionen kompatibel: Adobe Commerce On-Premise und Adobe Commerce in der Cloud-Infrastruktur 2.3.0-2.3.5-p1, 2.4.0 und 2.4.1.

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Leistungsprobleme auf der Seite mit der Kundenzittelliste:

* Doppeltes Laden der Anführungszeichenliste: zuerst mit der ganzen Seite, dann mit der Ajax-Anfrage.
* eine Schleife des Ladens der Anführungszeichen aus dem Plug-in.
* doppeltes Laden der Anführungszeichen, wenn das Anführungszeichen in den Schnappschuss konvertiert wurde.

<u>Zu reproduzierende Schritte</u>

1. einem Kunden mehr als 40 Anführungszeichen zugewiesen werden.
1. Melden Sie sich an und durchsuchen Sie die Seite **Meine Angebote** .

<u>Tatsächliches Ergebnis</u>

Die Antwortzeit zum vollständigen Laden des Inhalts der Seite **Meine Anführungszeichen** (Laden der Seite + der Daten, die im Raster angezeigt werden) beträgt ~ 45 Sekunden.

<u>Erwartetes Ergebnis</u>

Die Antwortzeit zum vollständigen Laden des Inhalts der Seite **Meine Anführungszeichen** sollte weniger als 45 Sekunden betragen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) verfügbare Patches.
