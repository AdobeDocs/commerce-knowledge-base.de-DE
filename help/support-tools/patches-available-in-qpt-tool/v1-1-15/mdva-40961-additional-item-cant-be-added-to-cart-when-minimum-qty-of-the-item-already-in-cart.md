---
title: 'MDVA-40961: Zusätzlicher Artikel kann nicht in den Warenkorb gelegt werden, wenn sich bereits eine Mindestmenge des Artikels im Warenkorb befindet'
description: Der MDVA-40961 Patch behebt das Problem, dass ein zusätzlicher Artikel nicht zum Warenkorb hinzugefügt werden kann, wenn die Mindestmenge des Artikels bereits im Warenkorb ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 installiert ist. Die Patch-ID lautet MDVA-40961. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
exl-id: fc90c2b6-f631-49ff-81b0-e41918dd79a7
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-40961: Zusätzlicher Artikel kann nicht in den Warenkorb gelegt werden, wenn sich bereits eine Mindestmenge des Artikels im Warenkorb befindet

Der MDVA-40961 Patch behebt das Problem, dass ein zusätzlicher Artikel nicht zum Warenkorb hinzugefügt werden kann, wenn die Mindestmenge des Artikels bereits im Warenkorb ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 installiert ist. Die Patch-ID lautet MDVA-40961. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Ein zusätzlicher Artikel kann nicht zum Warenkorb hinzugefügt werden, wenn die Mindestmenge des Artikels bereits im Warenkorb ist.

<u>Schritte zur Reproduktion</u>:

1. Legen Sie für ein einfaches Produkt mehr als eine **Mindestmenge im Warenkorb zulässig** fest (z. B. zwei).
1. Öffnen Sie das Produkt in der Storefront und fügen Sie zwei davon zum Warenkorb hinzu.
1. Bleiben Sie auf der Produktseite und fügen Sie eine weitere Version dieses Produkts zum Warenkorb hinzu.

<u>Erwartete Ergebnisse</u>:

Das dritte Produkt kann zum Warenkorb hinzugefügt werden, da es bereits die Mindestmenge enthält.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten die folgende Fehlermeldung: *Die wenigsten können Sie kaufen ist 2*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
