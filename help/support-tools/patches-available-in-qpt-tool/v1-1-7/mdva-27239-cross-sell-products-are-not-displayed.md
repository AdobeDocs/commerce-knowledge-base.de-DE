---
title: 'MDVA-27239: Crosssell-Produkte werden nicht angezeigt'
description: Der Patch MDVA-27239 behebt das Problem, dass Crosssell-Produkte nicht angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.3.6 behoben wurde.
exl-id: a0392a07-645d-4811-8547-2c67e20b6313
feature: Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# MDVA-27239: Crosssell-Produkte werden nicht angezeigt

Der Patch MDVA-27239 behebt das Problem, dass Crosssell-Produkte nicht angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.3.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4, 2.4.0

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.3.5-p2, 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Crosssell-Produkte werden nicht im Crosssell-Block auf der Warenkorbseite angezeigt.

<u>Voraussetzungen</u>:

1. Deaktivieren Sie das Magento_TargetRule-Modul oder entfernen Sie es aus dem Layout-Block Magento\TargetRule\Block\Checkout\Cart\Crosssell.
1. Produkt 1 erstellen.
1. Erstellen Sie eine Zeitplanaktualisierung für Produkt 1, sodass die neu erstellten Produkte eine andere row_id als entity_id haben.
1. Erstellen Sie Produkt 2, Produkt 3 und Produkt 4.
1. Legen Sie Produkt 3 als Crosssell für Produkt 4 fest.
1. Legen Sie Produkt 4 als Crosssell für Produkt 2 fest.

<u>Schritte zur Reproduktion</u>:

1. Fügen Sie Produkt 4 und Produkt 2 zum Warenkorb hinzu.
1. Überprüfen Sie die Warenkorbseite.

<u>Erwartete Ergebnisse</u>:

Produkt 3 wird im Crosssell-Block angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Crosssell-Block ist leer.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
