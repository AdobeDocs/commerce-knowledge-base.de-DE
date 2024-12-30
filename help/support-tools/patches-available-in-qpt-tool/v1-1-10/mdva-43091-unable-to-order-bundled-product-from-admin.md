---
title: 'MDVA-43091: Gebündeltes Produkt kann nicht vom Administrator bestellt werden'
description: Der Patch MDVA-43091 löst das Problem, dass Benutzende gebündelte Produkte nicht über Commerce Admin bestellen können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-43091. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
exl-id: 77dff356-4f75-4b06-b62b-5379a4eec273
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# MDVA-43091: Gebündeltes Produkt kann nicht vom Administrator bestellt werden

Der Patch MDVA-43091 löst das Problem, dass Benutzende gebündelte Produkte nicht über Commerce Admin bestellen können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-43091. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim Versuch, ein gebündeltes Produkt vom Administrator zu bestellen, wird der folgende Fehler ausgegeben: *Sie können für dieses Produkt keine Dezimalmenge verwenden.*

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie eine saubere Adobe Commerce.
1. Erstellen Sie zwei einfache Produkte.
1. Erstellen Sie ein gebündeltes Produkt mit zwei Optionen.
1. Erstellen Sie ein Kundenkonto im Frontend.
1. Wechseln Sie **Admin** > **Verkauf** > **Bestellungen** > **Neuen Auftrag erstellen**.
   * Wählen Sie das soeben erstellte Kundenkonto aus.
   * Versuchen Sie, das gebündelte Produkt zum Warenkorb hinzuzufügen.

<u>Erwartete Ergebnisse</u>:

Der Administrator kann dem Warenkorb das Produkt mit einer Menge hinzufügen.

<u>Tatsächliche Ergebnisse</u>:

Admin-Benutzende erhalten die folgende Fehlermeldung: *Sie können für dieses Produkt keine Dezimalzahl verwenden.*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in unserer Entwicklerdokumentation.
