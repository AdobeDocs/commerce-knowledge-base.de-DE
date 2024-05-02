---
title: '"MDVA-43232: Das Sortieren von Produkten im visuellen Merchandiser nach "Sonderpreis nach oben (oder unten)"verursacht einen Fehler.'
description: Der Patch MDVA-43232 behebt das Problem, bei dem das Sortieren von Produkten im visuellen Merchandiser nach "Sonderpreis nach oben"(oder "unten") beim Speichern der Kategorie einen Fehler verursacht. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-43232. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: e958a219-5e93-4ae4-94cb-f478f82ad060
feature: Categories, Merchandising, Orders, Personalization, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# MDVA-43232: Das Sortieren von Produkten im visuellen Merchandiser nach &quot;Special Price to Top&quot;(oder &quot;Bottom&quot;) verursacht einen Fehler

Der Patch MDVA-43232 behebt das Problem, bei dem das Sortieren von Produkten im visuellen Merchandiser nach &quot;Sonderpreis nach oben&quot;(oder &quot;unten&quot;) beim Speichern der Kategorie einen Fehler verursacht. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-43232. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4 - 2.4.3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Sortieren von Produkten im visuellen Merchandiser nach &quot;Sonderpreis nach oben&quot;(oder &quot;unten&quot;) führt beim Speichern der Kategorie zu einem Fehler.

<u>Zu reproduzierende Schritte</u>:

1. Stellen Sie sicher, dass es zwei Websites gibt.
1. Navigieren Sie zu **Stores** > **Konfiguration** > **Katalog** > **Preis** und legen Sie den Katalogpreisumfang = Website fest.
1. Navigieren Sie erneut zu **Stores** > **Konfiguration** > **Katalog** > **Visual Merchandiser** > **Sichtbare Attribute für Kategorieregeln** > und fügen Sie Sonderpreis hinzu.
1. Erstellen Sie ein einfaches Produkt und weisen Sie die Produkte beiden Websites zu.
1. Fügen Sie dem Standardbereich des Produkts einen Sonderpreis hinzu.
1. Wechseln Sie zum Bereich des anderen Stores und überschreiben Sie sowohl den Preis als auch den Sonderpreis dieses Produkts.
1. Führen Sie einen `catalog_product_price` reindex.
1. Navigieren Sie zu **Katalog** > **Kategorien** und erstellen Sie eine neue Kategorie.
1. Fügen Sie eine Kategorieregel hinzu, um Produkte mit einem Sonderpreis zu filtern.
1. Speichern Sie die Kategorie.
1. Legen Sie im Bereich Produkte in Kategorie die Option Sortierreihenfolge = Sonderpreis auf Oben (oder Unten) fest.
1. Speichern Sie die Kategorie erneut.

<u>Erwartete Ergebnisse</u>:

Die Kategorie wird fehlerfrei gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Eine Ausnahme wird ausgegeben:

```php
[2022-02-07T05:58:46.297621+00:00] report.CRITICAL: Exception: Item (Magento\Catalog\Model\Product\Interceptor) with the same ID "1" already exists. in /lib/internal/Magento/Framework/Data/Collection.php:407
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
