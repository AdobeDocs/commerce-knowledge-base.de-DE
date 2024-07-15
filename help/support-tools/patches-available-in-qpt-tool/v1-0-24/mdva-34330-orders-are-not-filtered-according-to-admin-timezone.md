---
title: "MDVA-34330: Bestellungen nicht nach Admin-Zeitzone gefiltert"
description: Der Patch MDVA-34330 behebt das Problem, dass Bestellungen nicht nach der Zeitzone des Administrators gefiltert werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24 installiert ist. Die Patch-ID lautet MDVA-34330. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.
exl-id: cb369ee3-60b0-4317-a448-0c4ed64f2816
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# MDVA-34330: Bestellungen nicht nach Admin-Zeitzone gefiltert

Der Patch MDVA-34330 behebt das Problem, dass Bestellungen nicht nach der Zeitzone des Administrators gefiltert werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24 installiert ist. Die Patch-ID lautet MDVA-34330. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce in Cloud-Infrastruktur 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungstypen) 2.3.1 - 2.4.2-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Bestellungen werden nicht nach der Admin-Zeitzone gefiltert.

<u>Zu reproduzierende Schritte</u>:

1. Wechseln Sie zu **Stores** > Einstellungen > **Konfiguration** > **Allgemein** und legen Sie die **Zeitzone** auf *Eastern Standard Time (America/New_York)* fest.
1. Neue Bestellung nach 00:00 UTC aufgeben
1. Wechseln Sie zu **Verkauf** > **Bestellungen** und filtern Sie nach dem aktuellen Datum.


<u>Erwartete Ergebnisse</u>:

Die heute nach 00:00 UTC platzierte Reihenfolge ist in gefilterten Ergebnissen sichtbar.

<u>Tatsächliche Ergebnisse</u>:

Die Reihenfolge fehlt in gefilterten Ergebnissen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungstyp die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitätspatches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Überprüfen Sie mithilfe des Qualitätssicherungswerkzeugs](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md), ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) verfügbare Patches.
