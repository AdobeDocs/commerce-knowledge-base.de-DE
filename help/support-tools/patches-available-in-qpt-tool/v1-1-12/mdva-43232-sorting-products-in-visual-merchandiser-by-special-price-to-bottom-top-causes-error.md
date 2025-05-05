---
title: 'MDVA-43232: Das Sortieren von Produkten im visuellen Merchandiser nach Sonderpreis nach oben (oder unten) verursacht einen Fehler'
description: Der Patch MDVA-43232 behebt das Problem, dass das Sortieren von Produkten in Visual Merchandiser nach Sonderpreis nach oben (oder unten) einen Fehler beim Speichern der Kategorie verursacht. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-43232. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
exl-id: e958a219-5e93-4ae4-94cb-f478f82ad060
feature: Categories, Merchandising, Orders, Personalization, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# MDVA-43232: Das Sortieren von Produkten im visuellen Merchandiser nach Sonderpreis nach oben (oder unten) verursacht einen Fehler

Der Patch MDVA-43232 behebt das Problem, dass das Sortieren von Produkten in Visual Merchandiser nach Sonderpreis nach oben (oder unten) einen Fehler beim Speichern der Kategorie verursacht. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-43232. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4 - 2.4.3

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Sortieren von Produkten im visuellen Merchandiser nach dem Sonderpreis nach oben (oder unten) verursacht einen Fehler beim Speichern der Kategorie.

<u>Schritte zur Reproduktion</u>:

1. Stellen Sie sicher, dass zwei Websites vorhanden sind.
1. Navigieren Sie zu **Stores** > **Configuration** > **CATALOG** > **PRICE** und legen Sie Katalogpreis Scope = Website fest.
1. Navigieren Sie erneut zu **Stores** > **Konfiguration** > **Katalog** > **Visual Merchandiser** > **Sichtbare Attribute für Kategorieregeln** > und fügen Sie einen Sonderpreis hinzu.
1. Erstellen Sie ein einfaches Produkt und weisen Sie die Produkte beiden Websites zu.
1. Fügen Sie dem Standardbereich des Produkts einen Sonderpreis hinzu.
1. Wechseln Sie zum Umfang des anderen Stores und überschreiben Sie sowohl den Preis als auch den Sonderpreis dieses Produkts.
1. Führen Sie eine `catalog_product_price` Neuindizierung durch.
1. Gehen Sie **Katalog** > **Kategorien** und erstellen Sie eine neue Kategorie.
1. Kategorieregel hinzufügen, um Produkte zu filtern, die einen Sonderpreis haben.
1. Speichern Sie die Kategorie.
1. Legen Sie im Abschnitt Produkte in Kategorie die Option Sortierreihenfolge = Sonderpreis auf Oben (oder Unten) fest.
1. Speichern Sie die Kategorie erneut.

<u>Erwartete Ergebnisse</u>:

Die Kategorie wird fehlerfrei gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Es wird eine Ausnahme ausgelöst:

```php
[2022-02-07T05:58:46.297621+00:00] report.CRITICAL: Exception: Item (Magento\Catalog\Model\Product\Interceptor) with the same ID "1" already exists. in /lib/internal/Magento/Framework/Data/Collection.php:407
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
