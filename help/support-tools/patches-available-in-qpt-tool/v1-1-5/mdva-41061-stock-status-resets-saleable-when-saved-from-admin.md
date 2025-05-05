---
title: 'MDVA-41061: Bestandsstatus wird auf „verkaufsfähig“ zurückgesetzt, wenn Produkt vom Administrator gespeichert wurde'
description: Mit dem Patch MDVA-41061 wird das Problem behoben, dass der Lagerstatus auf „verkaufbar“ zurückgesetzt wird, wenn das Produkt vom Administrator gespeichert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-41061. Die neueste Patch-Version ist in QPT 1.1.15 mit MDVA-41061-V3 Patch-ID verfügbar. Beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben wurde.
exl-id: fd71d3e5-685f-4987-b7e7-bfd86810d865
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-41061: Bestandsstatus wird auf „verkaufsfähig“ zurückgesetzt, wenn Produkt vom Administrator gespeichert wurde

Mit dem Patch MDVA-41061 wird das Problem behoben, dass der Lagerstatus auf „verkaufbar“ zurückgesetzt wird, wenn das Produkt vom Administrator gespeichert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-41061. Die neueste Patch-Version ist in QPT 1.1.15 mit MDVA-41061-V3 Patch-ID verfügbar. Beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.2-p2, 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Lagerstatus wird auf „verkaufbar“ zurückgesetzt, wenn das Produkt vom Administrator gespeichert wird.

<u>Voraussetzungen</u>:

Inventarmodule sind installiert.

<u>Schritte zur Reproduktion</u>:

1. Einfaches Produkt mit Menge = 1 erstellen.
1. Bestellen Sie mit dem in Schritt 1 erstellten Produkt.
1. Cron ausführen - Stellen Sie sicher, dass `inventory.reservations.updateSalabilityStatus` Warteschlange ausgeführt und der Produktlagerstatus in der `cataloginventory_stock_status`-Tabelle auf null geändert wurde.
1. Überprüfen Sie das Produkt im Frontend. Sie sollte als „Nicht **&quot; gekennzeichnet**.
1. Produkt ohne Änderungen im Admin-Bereich speichern.

<u>Erwartete Ergebnisse</u>:

* Der Lagerstatus sollte nicht aktualisiert werden.
* Das Produkt sollte **nicht vorrätig** am Frontend sein.

<u>Tatsächliche Ergebnisse</u>:

* Einfaches Produkt wird im Frontend mit **Auf Lager** gekennzeichnet.
* Benutzende erhalten *Die angeforderte Menge ist nicht verfügbar* Meldung, wenn sie versuchen, sie zum Warenkorb hinzuzufügen.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
