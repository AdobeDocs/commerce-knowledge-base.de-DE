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

Der Patch MDVA-33970 behebt das Problem, dass anstelle der lokalisierten Währung in einem Kreditmemo ein Dollarzeichen ($) angezeigt wurde. Dies geschieht, wenn eine **Webseite** Der Gültigkeitsbereich wird für eine **Preis** -Attribut.

Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.3 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce auf Cloud-Infrastruktur 2.3.4-p2

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.3.4 - 2.4.1-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Voraussetzungen</u>:

Für dieses Beispiel werden die folgenden Einstellungen verwendet:

* 2 Websites sind vorhanden - jeder verfügt über eine **Store** und **Store-Ansicht**.
* Die **Standardkonfiguration** den Singapur-Dollar als **Währung** (**Stores > Konfiguration > Allgemein > Währungseinstellungen**):
   * **Basiswährung** = *Singapur, Dollar*
   * **Standardanzeigewährung** = *Singapur, Dollar*
   * **Zulässige Währungen** = *Singapur, Dollar*
* **Website 1** hat eine **Standardkonfiguration**.
* **Website 2** hat den malaysischen Ringgit als **Währung**:
   * **Basiswährung** = *Malaysia Ringgit*
   * **Standardanzeigewährung** = *Malaysia Ringgit*
   * **Zulässige Währungen** = *Malaysia Ringgit*
* Navigieren Sie zu **Stores > Währungssymbole**, und legen Sie fest:
   * **MYR (Malaysischer Ringgit)** = *RM*
   * **SGD (Singapur-Dollar)** = *SGD* (**Use Standard** = *Aktiviert*)
* Einige **Produkt** vorhanden ist.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine **Bestellung** aus dem **Website 2** (Sie können ihn als Standard einrichten, um zusätzliche Einstellungen zu vermeiden).
1. Anmelden bei **Admin**.
1. Öffnen Sie die neu erstellte Bestellung.
1. Stellen Sie sicher, dass die **Währungssymbol** = *RM*.
1. Erstellen Sie eine **Rechnung**.
1. Stellen Sie sicher, dass die **Währungssymbol** = *RM* in der Rechnung.
1. Erstellen Sie eine **Credit Memo**.
1. Stellen Sie sicher, dass die **Währungssymbol**  ** ** = *RM* im **Credit Memo**.
1. Öffnen Sie die **Credit Memos** Registerkarte in **Bestellung**.
1. Überprüfen Sie die **Währungssymbol** im Raster.
1. Öffnen **Verkauf > Credit Memos**.
1. Überprüfen Sie die **Währungssymbol** im Raster.

<u>Erwartete Ergebnisse</u>:

Das richtige lokalisierte Währungssymbol wird wie erwartet verwendet.

<u>Tatsächliche Ergebnisse</u>:

Das Dollarzeichen ($) wird verwendet, auch wenn es nicht in den Admin-Einstellungen eingerichtet ist.

## Wenden Sie den Patch an

Verwenden Sie je nach Adobe Commerce-Produkt die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) Abschnitt.
