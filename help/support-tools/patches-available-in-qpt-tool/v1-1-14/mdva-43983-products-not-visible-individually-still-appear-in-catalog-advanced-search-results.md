---
title: '"MDVA-43983: Produkte, die als "Nicht einzeln sichtbar"festgelegt sind, werden in den Suchergebnissen angezeigt."'
description: Der Patch MDVA-43983 behebt das Problem, dass die Produkte, die als "Nicht sichtbar individuell"festgelegt sind, weiterhin in den erweiterten Suchergebnissen des Katalogs angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-43983. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: 2599fb6c-5b27-461b-9740-f586ae7df9f5
feature: Catalog Management, Products, Search
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-43983: Produkte, die als &quot;Nicht einzeln sichtbar&quot;festgelegt sind, werden in den Suchergebnissen angezeigt

Der Patch MDVA-43983 behebt das Problem, dass die Produkte, die als &quot;Nicht sichtbar individuell&quot;festgelegt sind, weiterhin in den erweiterten Suchergebnissen des Katalogs angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-43983. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Produkte, die als &quot;Nicht einzeln sichtbar&quot;festgelegt sind, werden weiterhin in den erweiterten Suchergebnissen des Katalogs angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Attribut mit dem Eingabetyp &quot;Katalog&quot;für Store Owner **als** Dropdown **oder** visuelles Muster **(z. B. Farbe).**
1. Stellen Sie **In der Suche** auf **Ja** und **In der erweiterten Suche anzeigen** auf **Ja** ein.
1. Fügen Sie einige Attributoptionen hinzu.
1. Erstellen Sie Produkte mit **Sichtbarkeit** als **Nicht einzeln sichtbar**.
1. Farbattribute zuweisen - Optionen.
1. Rufen Sie die Seite **Erweiterte Katalogsuche** auf der Storefront auf.
1. Wählen Sie im Feld Farbattribut nur die Option Farbattribut aus und lassen Sie die übrigen Felder leer oder so, wie es ist.
1. Senden Sie ein erweitertes Suchformular.
1. Beobachten Sie die Suchergebnisse.

<u>Erwartete Ergebnisse</u>:

Produkte, die als &quot;Nicht einzeln sichtbar&quot;festgelegt sind, werden nicht in den erweiterten Suchergebnissen des Katalogs angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Produkte, die als &quot;Nicht einzeln sichtbar&quot;festgelegt sind, werden in den erweiterten Suchergebnissen des Katalogs angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
