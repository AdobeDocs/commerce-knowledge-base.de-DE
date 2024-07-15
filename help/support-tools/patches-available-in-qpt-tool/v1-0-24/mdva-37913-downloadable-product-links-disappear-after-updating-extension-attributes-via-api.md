---
title: "MDVA-37913: Links zu Produktdownloads verschwinden nach der Aktualisierung von Erweiterungsattributen über API"
description: Der Patch MDVA-37913 für behebt das Problem, dass die herunterladbaren Produktlinks nach der Aktualisierung von Erweiterungsattributen über API verschwinden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24 installiert ist. Die Patch-ID lautet MDVA-37913. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.
exl-id: e4b2cf59-5c35-4a28-a63e-15cd7d0d5a5d
feature: REST, Attributes, Extensions, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# MDVA-37913: Links zu Produktdownloads verschwinden, nachdem Erweiterungsattribute über API aktualisiert wurden

Der Patch MDVA-37913 für behebt das Problem, dass die herunterladbaren Produktlinks nach der Aktualisierung von Erweiterungsattributen über API verschwinden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24 installiert ist. Die Patch-ID lautet MDVA-37913. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben sein soll.


## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
Adobe Commerce in Cloud-Infrastruktur 2.3.6

**Kompatibel mit Adobe Commerce-Versionen:**
Adobe Commerce On-Premise und Adobe Commerce über Cloud-Infrastruktur 2.3.0 - 2.4.0-p1
>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.


## Problem

Herunterladbare Produkt-Links werden nach der Aktualisierung von Erweiterungsattributen über die API nicht mehr angezeigt.

<u>Voraussetzungen</u>:
Herunterladbares Produkt mit Downloadlinks.

<u>Zu reproduzierende Schritte</u>:

1. Aktualisieren Sie die Erweiterungsattribute mithilfe einer Anfrage wie dieser:

```JSON
{
    "product": {
        "extension_attributes": {
            "stock_item": {
                "is_in_stock": true,
                "qty": 100
            }
        }
    }
}
```

<u>Erwartete Ergebnisse</u>:<br>
Das Produkt wird aktualisiert, nicht alle Downloadlinks entfernt.

<u>Tatsächliche Ergebnisse</u>:<br>
Das Produkt wurde aktualisiert, aber alle Downloadlinks wurden entfernt.


## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* Adobe Commerce in der Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html)

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster in unserer Wissensdatenbank finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Weitere Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Patches verfügbar im QPT-Tool](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) in unserer Support-Wissensdatenbank.
