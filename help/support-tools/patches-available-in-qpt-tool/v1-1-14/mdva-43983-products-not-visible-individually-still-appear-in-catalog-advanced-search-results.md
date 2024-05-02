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

Der Patch MDVA-43983 behebt das Problem, dass die Produkte, die als &quot;Nicht sichtbar individuell&quot;festgelegt sind, weiterhin in den erweiterten Suchergebnissen des Katalogs angezeigt werden. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 ist installiert. Die Patch-ID lautet MDVA-43983. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Produkte, die als &quot;Nicht einzeln sichtbar&quot;festgelegt sind, werden weiterhin in den erweiterten Suchergebnissen des Katalogs angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Attribut mit **Katalogeingabetyp für Store Owner** as **Dropdown** oder **Visuelles Muster** (z. B. Farbe).
1. Satz **Verwendung in der Suche** as **Ja** und **In erweiterter Suche sichtbar** as **Ja**.
1. Fügen Sie einige Attributoptionen hinzu.
1. Produkte mit **Sichtbarkeit** as **Individuell nicht sichtbar**.
1. Farbattribute zuweisen - Optionen.
1. Navigieren Sie zu **Erweiterte Katalogsuche** auf der Storefront angezeigt.
1. Wählen Sie im Feld Farbattribut nur die Option Farbattribut aus und lassen Sie die übrigen Felder leer oder so, wie es ist.
1. Senden Sie ein erweitertes Suchformular.
1. Beobachten Sie die Suchergebnisse.

<u>Erwartete Ergebnisse</u>:

Produkte, die als &quot;Nicht einzeln sichtbar&quot;festgelegt sind, werden nicht in den erweiterten Suchergebnissen des Katalogs angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Produkte, die als &quot;Nicht einzeln sichtbar&quot;festgelegt sind, werden in den erweiterten Suchergebnissen des Katalogs angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
