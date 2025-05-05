---
title: 'MDVA-42507: Der Vollseiten-Cache wird nach der Anwendung der Staging-Aktualisierung für die Warenkorbregel bereinigt'
description: Der Patch MDVA-42507 löst das Problem, dass der Vollseiten-Cache nach der Anwendung der Staging-Aktualisierung für die Warenkorbregel bereinigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-42507. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
exl-id: 9303d488-428b-4565-b9ea-469c34856dce
feature: Cache, Categories, Orders, Shopping Cart, Staging
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-42507: Der Vollseiten-Cache wird nach der Anwendung der Staging-Aktualisierung für die Warenkorbregel bereinigt

Der Patch MDVA-42507 löst das Problem, dass der Vollseiten-Cache nach der Anwendung der Staging-Aktualisierung für die Warenkorbregel bereinigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-42507. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der vollständige Seiten-Cache wird nach der Anwendung der Staging-Aktualisierung für die Warenkorbregel bereinigt.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie den Entwicklermodus.
1. Öffnen Sie mehrere Produkt- und Kategorieseiten und überprüfen Sie (über Kopfzeilen), ob sie aus dem Cache geladen werden.
1. Wenden Sie eine beliebige Staging-Aktualisierung für die Warenkorbregel an.
1. Überprüfen Sie, ob die Kategorie- und Produktseiten weiterhin aus dem Cache geladen werden.

<u>Erwartete Ergebnisse</u>:

Der vollständige Seiten-Cache wird nach der Anwendung der Staging-Aktualisierung für die Warenkorbregel NICHT bereinigt.

<u>Tatsächliche Ergebnisse</u>:

Der vollständige Seiten-Cache wird nach der Anwendung der Staging-Aktualisierung für die Warenkorbregel bereinigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
