---
title: 'MDVA-37592: Sortierung nach Preis funktioniert nicht für Produkte mit Preis Null'
description: Der MDVA-37592 Adobe Commerce Patch löst das Problem, dass die Sortierung nach Preis bei Produkten mit einem Preis Null, der einem freigegebenen Katalog zugewiesen ist, nicht korrekt funktioniert. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0 installiert ist. Die Patch-ID lautet MDVA-37592. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
exl-id: 30ac1e87-c32d-4e79-9ed9-d1861061d760
feature: B2B, Catalog Management, Categories, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# MDVA-37592: Sortierung nach Preis funktioniert nicht für Produkte mit Preis Null

Der MDVA-37592 Adobe Commerce Patch löst das Problem, dass die Sortierung nach Preis bei Produkten mit einem Preis Null, der einem freigegebenen Katalog zugewiesen ist, nicht korrekt funktioniert. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0 installiert ist. Die Patch-ID lautet MDVA-37592. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce auf unserer Cloud-Architektur 2.4.0-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungstypen) 2.3.6-2.4.2-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Sortierung nach Preis funktioniert bei Produkten mit einem Preis Null, der einem freigegebenen Katalog zugewiesen ist, nicht ordnungsgemäß.

<u>Voraussetzungen</u>:

B2B ist installiert.

<u>Schritte zur Reproduktion</u>:

1. Freigegebenen Katalog aktivieren.
1. Erstellen Sie vier Produkte mit den folgenden Preisen und weisen Sie sie einer Kategorie zu: 50 $, 60 $, 70 $ und 80 $.
1. Erstellen Sie einen freigegebenen Katalog mit den oben genannten Produkten.
1. Setzen Sie den benutzerdefinierten Preis für das Produkt mit einem Preis von 70 $ auf null.
1. Erstellen Sie nun einen Firmenbenutzer und weisen Sie ihn dem soeben erstellten freigegebenen Katalog zu.
1. Melden Sie sich mit dem Unternehmenskonto an und navigieren Sie zur Kategorie, der die Produkte zugewiesen sind.
1. Sortieren Sie nach Preis.

<u>Erwartete Ergebnisse</u>:

Das Produkt mit dem Preis Null wird korrekt sortiert.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt mit dem Preis Null wird NICHT korrekt sortiert. Stattdessen wird nach dem ursprünglichen Preis sortiert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungstyp die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf unserer Cloud-Architektur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Überprüfen Sie mit dem Quality Patches Tool, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Weitere Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Patches im QPT-Tool verfügbar](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
