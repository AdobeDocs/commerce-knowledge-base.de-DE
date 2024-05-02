---
title: "MDVA-38468: Empfangen einer Fehlermeldung beim Speichern der CMS-Seite"
description: 'Der Adobe Commerce-Patch MDVA-38468 behebt das Problem, bei dem Benutzer die Fehlermeldung erhalten: *Element mit der gleichen ID "PAGE_ID"ist bereits vorhanden* beim Speichern einer CMS-Seite. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.26 installiert ist. Die Patch-ID lautet MDVA-38468. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.3.6 behoben wurde."'
exl-id: 7fe80308-50b7-4786-a43c-cce607eb606c
feature: CMS, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-38468: Beim Speichern der CMS-Seite eine Fehlermeldung erhalten

Der MDVA-38468 Adobe Commerce Patch behebt das Problem, dass Benutzer die Fehlermeldung erhalten: *Ein Element mit derselben ID &quot;PAGE_ID&quot;ist bereits vorhanden,* beim Speichern einer CMS-Seite. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.26 ist installiert. Die Patch-ID lautet MDVA-38468. Beachten Sie, dass das Problem in Adobe Commerce 2.3.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
Adobe Commerce auf Cloud-Infrastruktur 2.3.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**
Adobe Commerce vor Ort und Adobe Commerce über Cloud-Infrastruktur 2.3.2-2.3.5-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Beim Versuch, eine CMS-Seite zu speichern, erhalten Sie die folgende Fehlermeldung: *Ein Element mit derselben ID &quot;PAGE_ID&quot;ist bereits vorhanden.*

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine neue Website + Store + Storeview.
1. Erstellen Sie eine weitere Website + Store + Storeview.
1. Navigieren Sie zu **Inhalt** > **Hierarchie** > Fügen Sie eine vorhandene CMS-Seite der Hierarchiestruktur hinzu.
1. Navigieren Sie zu **Inhalt** > **Seiten** > **Neue Seite hinzufügen**:
   * Fügen Sie einen beliebigen Titel hinzu.
   * Weisen Sie in Seite in Websites beiden erstellten Storeviews zu.
   * Weisen Sie im Abschnitt Hierarchie einer beliebigen Kategorie zu.
   * **Speichern und fortfahren Bearbeiten**.

<u>Erwartete Ergebnisse</u>:

Die Seite wird ohne Fehler gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Die Seite wird gespeichert, Sie erhalten jedoch die folgende Fehlermeldung: *Element (Magento\VersionsCms\Model\Hierarchy\Node) mit derselben ID &quot;PAGE_ID&quot;ist bereits vorhanden.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) Abschnitt.
