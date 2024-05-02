---
title: '"MDVA-39482: Das Produkt wird nicht vorrätig eingeführt, wenn es mit "0"Menge mit aktivierten Rückständen importiert wird."'
description: Der MDVA-39482 behebt das Problem, dass das Produkt nicht mehr vorrätig ist, wenn es mit "0"importiert wird, wenn MSI und Rückorder aktiviert sind und der Schwellenwert für nicht vorrätige Waren auf einen Minuswert gesetzt ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-39482. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: 2caf461c-993d-48b3-bc47-3fa1d014deaf
feature: Data Import/Export, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-39482: Das Produkt wird nicht mehr vorrätig eingeführt, wenn es mit &quot;0&quot; Menge importiert wird und die Backorder aktiviert sind

Der MDVA-39482 behebt das Problem, dass das Produkt nicht mehr vorrätig ist, wenn es mit &quot;0&quot;importiert wird, wenn MSI und Rückorder aktiviert sind und der Schwellenwert für nicht vorrätige Waren auf einen Minuswert gesetzt ist. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4 ist installiert. Die Patch-ID lautet MDVA-39482. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Produkt wird nicht mehr vorrätig, wenn es mit der Menge &quot;0&quot;importiert wird, wenn MSI und Rückorder aktiviert sind und der Schwellenwert für nicht vorrätige Produkte auf einen Minuswert gesetzt ist.

<u>Voraussetzungen</u>:

1. MSI und Beispieldaten müssen installiert sein.
1. Navigieren Sie zu **Stores** > **Konfigurationen** > **Katalog** > **Bestand**:
   * Legen Sie &quot;Rückläufe&quot;auf &quot;Menge unter 0 zulassen&quot;fest.
   * Nicht vorrätiger Schwellenwert auf &quot;-10&quot; setzen

<u>Zu reproduzierende Schritte</u>:

1. Stellen Sie sicher, dass die SKU **Auf Lager** und hat eine Menge **24 MB01**.
1. Importieren Sie die CSV-Datei der Lagerquellen. Stellen Sie sicher, dass Sie unter Entitätstyp &quot;Stock Sources&quot;auswählen:

   ```code panel
   sku,qty,out_of_stock_qty
   24-MB01,0,-10
   ```

1. Überprüfen Sie den Lagerstatus des Produkts, nachdem die Lagerquellen importiert wurden.

<u>Erwartete Ergebnisse</u>:

24 MB01 ist **Auf Lager** in Storefront.

<u>Tatsächliche Ergebnisse</u>:

24 MB01 ist **Nicht auf Lager** in Storefront.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) Abschnitt.
