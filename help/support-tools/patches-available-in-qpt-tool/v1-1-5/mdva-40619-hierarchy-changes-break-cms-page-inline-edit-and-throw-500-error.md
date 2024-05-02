---
title: "MDVA-40619: Hierarchieänderungen unterbrechen die Inline-Bearbeitung der CMS-Seite und verursachen 500 Fehler."
description: Der Patch MDVA-40619 behebt das Problem, dass die CMS-Seitenhierarchie die CMS-Seite inline bearbeiten und "500-Fehler"ausgeben kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-40619. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: c003d845-1ba0-49c0-9f1a-a4b0ec00f30c
feature: CMS
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# MDVA-40619: Hierarchieänderungen unterbrechen die Inline-Bearbeitung der CMS-Seite und verursachen 500 Fehler

Der Patch MDVA-40619 behebt das Problem, dass die CMS-Seitenhierarchie die CMS-Seite inline bearbeiten und &quot;500-Fehler&quot;ausgeben kann. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 ist installiert. Die Patch-ID lautet MDVA-40619. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Änderungen an der CMS-Seitenhierarchie unterbrechen die Inline-Bearbeitung der CMS-Seite und verursachen &quot;500-Fehler&quot;.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zum Admin Panel > **Inhalt** > **Hierarchie**.
1. Wählen Sie &quot;Standard-Store-Ansicht&quot;.
1. Deaktivieren Sie &quot;Hierarchie des übergeordneten Knotens verwenden&quot;.
1. Manuelles Auswählen der Seite und Klicken auf **Speichern**.
1. Gehen Sie dann zu **Inhalt** > **Seiten**.
1. Versuchen Sie, eine beliebige CMS-Seite aus dem Raster zu bearbeiten.
1. Klicks **Speichern**.

<u>Erwartete Ergebnisse</u>:

Die Seite wurde erfolgreich gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten den folgenden Fehler:

*Ein technisches Problem mit dem Server hat einen Fehler verursacht. Versuchen Sie es noch einmal, mit dem fortzufahren, was Sie getan haben. Wenn das Problem weiterhin besteht, versuchen Sie es später erneut.*

`Error: Call to a member function getData() on null in /magento2ee/app/code/Magento/VersionsCms/Controller/Adminhtml/Cms/Page/InlineEdit/Plugin.php:62`

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) Abschnitt.
