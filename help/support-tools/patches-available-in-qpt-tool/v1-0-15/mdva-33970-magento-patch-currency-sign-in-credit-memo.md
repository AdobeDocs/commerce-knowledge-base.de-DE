---
title: "MDVA-33970 Patch: Währungszeichen in Credit Memo"
description: Der Patch MDVA-33970 behebt das Problem, dass anstelle der lokalisierten Währung in einem Kreditmemo ein Dollarzeichen ($) angezeigt wurde. Dies tritt auf, wenn ein Bereich **Website** für ein Attribut **Preis** verwendet wird.
exl-id: 47a03067-86ef-4a55-8c21-921781062b53
feature: Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# MDVA-33970 Patch: Währungszeichen im Kreditmemo

Der Patch MDVA-33970 behebt das Problem, dass anstelle der lokalisierten Währung in einem Kreditmemo ein Dollarzeichen ($) angezeigt wurde. Dies tritt auf, wenn ein Gültigkeitsbereich von **Website** für ein Attribut **Preis** verwendet wird.

Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.3 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce für die Cloud-Infrastruktur 2.3.4-p2

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce für Cloud-Infrastruktur und Adobe Commerce On-Premise 2.3.4 - 2.4.1-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Precondition</u>:

Für dieses Beispiel werden die folgenden Einstellungen verwendet:

* 2 Websites sind vorhanden - jede hat einen **Store** und eine **Store-Ansicht**.
* Die Standardkonfiguration **von** hat den Singapur-Dollar als **Währung** (**Speicher > Konfiguration > Allgemein > Währungseinstellungen**):
   * **Basiswährung** = *Singapur-Dollar*
   * **Standardanzeigewährung** = *Singapur-Dollar*
   * **Zulässige Währungen** = *Singapur-Dollar*
* **Website 1** hat eine **Standardkonfiguration**.
* **Website 2** hat den malaysischen Ringgit als **Währung**:
   * **Basiswährung** = *Malaysischer Ringgit*
   * **Standardanzeigewährung** = *Malaysischer Ringgit*
   * **Zulässige Währungen** = *Malaysischer Ringgit*
* Wechseln Sie zu **Stores > Währungssymbole** und legen Sie Folgendes fest:
   * **MYR (Malaysischer Ringgit)** = *RM*
   * **SGD (Singapur-Dollar)** = *SGD* (**Use Standard** = *Checked*)
* Einige **Produkt** sind vorhanden.

<u>Zu reproduzierende Schritte</u>:

1. Nehmen Sie eine **Bestellung** von der **Website 2** vor (Sie können sie als Standard einrichten, um zusätzliche Einstellungen zu vermeiden).
1. Melden Sie sich bei **Admin** an.
1. Öffnen Sie die neu erstellte Bestellung.
1. Überprüfen Sie, ob das **Währungssymbol** = *RM* ist.
1. Erstellen Sie eine **Rechnung**.
1. Überprüfen Sie, ob das **Währungssymbol** = *RM* in der Rechnung enthalten ist.
1. Erstellen Sie ein **Credit Memo**.
1. Überprüfen Sie, ob das **Währungssymbol** ** ** = *RM* im **Credit Memo** enthalten ist.
1. Öffnen Sie die Registerkarte **KreditMemos** in **Bestellung**.
1. Überprüfen Sie das **Währungssymbol** im Raster.
1. Öffnen Sie **Verkauf > Kreditkarten**.
1. Überprüfen Sie das **Währungssymbol** im Raster.

<u>Erwartete Ergebnisse</u>:

Das richtige lokalisierte Währungssymbol wird wie erwartet verwendet.

<u>Tatsächliche Ergebnisse</u>:

Das Dollarzeichen ($) wird verwendet, auch wenn es nicht in den Admin-Einstellungen eingerichtet ist.

## Wenden Sie den Patch an

Verwenden Sie je nach Adobe Commerce-Produkt die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
