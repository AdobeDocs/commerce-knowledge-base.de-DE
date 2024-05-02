---
title: 'MDVA-34012 Patch: Attribut Checkbox changes in error'
description: Der Patch MDVA-34012 behebt das Problem, bei dem das Kontrollkästchen für ein Attribut nach einem fehlgeschlagenen Zeitplanupdate geändert wird.
exl-id: 1a8f1bea-9b6a-4984-b9f0-b2b9ceb6688f
feature: Attributes
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# MDVA-34012 Patch: Attribut-Checkbox-Änderungen in Fehler

Der Patch MDVA-34012 behebt das Problem, bei dem das Kontrollkästchen für ein Attribut nach einem fehlgeschlagenen Zeitplanupdate geändert wird.

Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.17 ist installiert. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.3 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce auf Cloud-Infrastruktur 2.3.5-p2

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.3.1 - 2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei Admin an und navigieren Sie zu **Katalog > Produkte**.
1. Bearbeiten Sie ein beliebiges einfaches Produkt.
1. Ändern Sie die Store-Ansicht in eine bestimmte Store-Ansicht.
1. Speichern Sie das Produkt mit der **Standardwert verwenden** für ein Attribut aktiviert wurde (Beispiel: **Produkt aktivieren** -Attribut).
1. Klicken Sie auf **Neue Aktualisierung planen** , um einige Änderungen zu planen (Beispiel: **Preis** oder **Sonderpreis** für eine bestimmte Store-Ansicht).
1. Warten Sie, bis die Änderungen abgeschlossen sind.
1. Überprüfen Sie das Produkt. Das Kontrollkästchen sollte deaktiviert sein und einen bestimmten Store-Attributwert aufweisen.

<u>Erwartete Ergebnisse</u>:

Das Kontrollkästchen für das Attribut sollte unverändert bleiben und wird nach der Zeitplanaktualisierung nicht wie erwartet geändert.

<u>Tatsächliche Ergebnisse</u>:

Das Kontrollkästchen für das Attribut wird nach der Aktualisierung des Zeitplans geändert.

## Wenden Sie den Patch an

Verwenden Sie je nach Adobe Commerce-Produkt die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) Abschnitt.
