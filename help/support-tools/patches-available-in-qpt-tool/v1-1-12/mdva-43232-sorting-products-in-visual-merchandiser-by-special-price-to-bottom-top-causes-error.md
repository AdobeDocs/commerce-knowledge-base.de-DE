---
title: '"MDVA-43232: Das Sortieren von Produkten im visuellen Merchandiser nach "Sonderpreis nach oben (oder unten)"verursacht einen Fehler.'
description: Der Patch MDVA-43232 behebt das Problem, bei dem das Sortieren von Produkten im visuellen Merchandiser nach "Sonderpreis nach oben"(oder "unten") beim Speichern der Kategorie einen Fehler verursacht. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-43232. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
exl-id: e958a219-5e93-4ae4-94cb-f478f82ad060
feature: Categories, Merchandising, Orders, Personalization, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# MDVA-43232: Das Sortieren von Produkten im visuellen Merchandiser nach &quot;Special Price to Top&quot;(oder &quot;Bottom&quot;) verursacht einen Fehler

Der Patch MDVA-43232 behebt das Problem, bei dem das Sortieren von Produkten im visuellen Merchandiser nach &quot;Sonderpreis nach oben&quot;(oder &quot;unten&quot;) beim Speichern der Kategorie einen Fehler verursacht. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-43232. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4 - 2.4.3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Sortieren von Produkten im visuellen Merchandiser nach &quot;Sonderpreis nach oben&quot;(oder &quot;unten&quot;) führt beim Speichern der Kategorie zu einem Fehler.

<u>Zu reproduzierende Schritte</u>:

1. Stellen Sie sicher, dass es zwei Websites gibt.
1. Navigieren Sie zu &quot;**Stores**&quot;> &quot;**Konfiguration**&quot;> &quot;**Katalog**&quot;> &quot;**Preis**&quot;und legen Sie den Umfang des Katalogpreises = Website fest.
1. Navigieren Sie erneut zu &quot;**Stores**&quot;> &quot;**Konfiguration**&quot;> &quot;**Katalog**&quot;> &quot;**Visual Merchandiser**&quot;> &quot;**Sichtbare Attribute für Kategorieregeln**&quot; und fügen Sie Sonderpreis hinzu.
1. Erstellen Sie ein einfaches Produkt und weisen Sie die Produkte beiden Websites zu.
1. Fügen Sie dem Standardbereich des Produkts einen Sonderpreis hinzu.
1. Wechseln Sie zum Bereich des anderen Stores und überschreiben Sie sowohl den Preis als auch den Sonderpreis dieses Produkts.
1. Führen Sie eine Neuindizierung des Werts `catalog_product_price` durch.
1. Gehen Sie zu **Katalog** > **Kategorien** und erstellen Sie eine neue Kategorie.
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

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) verfügbar sind, in unserer Entwicklerdokumentation.
