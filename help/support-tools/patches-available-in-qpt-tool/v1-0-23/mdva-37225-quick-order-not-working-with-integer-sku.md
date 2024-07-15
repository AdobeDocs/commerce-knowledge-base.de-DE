---
title: "MDVA-37225: Quick order not working with integer SKU"
description: Der Qualitäts-Patch MDVA-37225 für Adobe Commerce behebt das Problem, dass die Seite beim Erstellen einer schnellen Bestellung nicht geladen wird, wenn in importierten SKUs ein ganzzahliger Wert vorhanden ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 installiert ist. Die Patch-ID lautet MDVA-37225. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.3 behoben werden soll.
exl-id: ecd2b9d7-ca68-4372-b0c5-55e2a3301586
feature: B2B, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# MDVA-37225: Schnellbestellung funktioniert nicht mit Integer-SKU

Der Qualitäts-Patch MDVA-37225 für Adobe Commerce behebt das Problem, dass die Seite beim Erstellen einer schnellen Bestellung nicht geladen wird, wenn in importierten SKUs ein ganzzahliger Wert vorhanden ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 installiert ist. Die Patch-ID lautet MDVA-37225. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.3 behoben werden soll.

## Betroffene Produkte und Versionen

* Der Patch wurde für Adobe Commerce in der Cloud-Infrastruktur 2.4.1-p1 entwickelt.
* Der Patch ist auch mit Adobe Commerce On-Premise und Adobe Commerce in der Cloud-Infrastruktur 2.4.1-2.4.2-p1 kompatibel

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Voraussetzung</u>:

Adobe Commerce mit installiertem B2B-Modul

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie die Funktion für schnelle B2B-Bestellungen.
1. Erstellen Sie vier einfache Produkte mit SKUs (Beispiel-SKUs: *00100*, *001E002*, *001E02C* und *7100824*).
1. Gehen Sie zur Seite &quot;``<storefront_url>/quickorder``&quot;im Frontend und versuchen Sie, eine Bestellung mithilfe einer CSV-Datei mit diesem Beispielinhalt zu erstellen:

| sku | qty |
|---|---|
| 00100 | 1 |


<u>Erwartete Ergebnisse</u>:

Das Produkt (Beispiel: Produkt mit SKU = *00100*) wird wie erwartet zum Warenkorb hinzugefügt.

<u>Tatsächliche Ergebnisse</u>:

Die Seite wird nicht geladen und dem Warenkorb werden keine Produkte hinzugefügt.


## Wenden Sie den Patch an

Um einzelne Patches anzuwenden, verwenden Sie je nach Adobe Commerce-Produkt die folgenden Links in unserer Entwicklerdokumentation:

* Adobe Commerce und Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* Adobe Commerce in der Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html)

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster in unserer Wissensdatenbank finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Weitere Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Patches verfügbar im QPT-Tool](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) in unserer Support-Wissensdatenbank.
