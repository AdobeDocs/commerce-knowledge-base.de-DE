---
title: "MDVA-40545: Es wird nur der erste Knoten für eine Seite abgerufen."
description: Der MDVA-40545-Patch behebt das Problem, dass nur der erste Knoten für eine Seite abgerufen wird, selbst wenn mehrere Knoten für dieselbe Seite vorhanden sind. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-40545. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: ac7aaed9-5e81-45fe-b699-40d9c086a05c
feature: CMS, Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-40545: Nur der erste Knoten für eine Seite wird abgerufen

Der MDVA-40545-Patch behebt das Problem, dass nur der erste Knoten für eine Seite abgerufen wird, selbst wenn mehrere Knoten für dieselbe Seite vorhanden sind. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 ist installiert. Die Patch-ID lautet MDVA-40545. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Es wird nur der erste Knoten für eine Seite abgerufen, selbst wenn für dieselbe Seite mehrere Knoten vorhanden sind.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie im Admin Panel zu **Hierarchie** und fügen Sie zwei Menüelemente/Knoten hinzu.
1. Fügen Sie jedem Knoten dieselbe CMS-Seite hinzu.
1. Löschen Sie den Cache und überprüfen Sie das Frontend.
1. Überprüfen Sie den Link und die Breadcrumbs für das erste hinzugefügte Untermenü.
1. Überprüfen Sie den Link und die Breadcrumbs für das zweite hinzugefügte Untermenü.

<u>Erwartete Ergebnisse</u>:

Breadcrumbs und Link im zweiten Untermenü sind für den zweiten Knoten relevant.

<u>Tatsächliche Ergebnisse</u>:

Breadcrumbs und Link im zweiten Untermenü sind mit dem ersten Untermenü identisch.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) Abschnitt.
