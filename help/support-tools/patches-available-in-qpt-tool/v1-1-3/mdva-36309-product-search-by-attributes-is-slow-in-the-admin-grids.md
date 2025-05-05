---
title: 'MDVA-36309: Die Produktsuche nach Attributen ist in Admin-Rastern langsam'
description: Der Patch MDVA-36309 löst das Problem, dass die Produktsuche nach Attributen in den Admin-Rastern langsam ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3 installiert ist. Die Patch-ID lautet MDVA-36309. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
exl-id: 5e6b426b-201d-44a2-8c03-8ed5de8ed203
feature: Admin Workspace, Attributes, Products, Search
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# MDVA-36309: Die Produktsuche nach Attributen ist in Admin-Rastern langsam

Der Patch MDVA-36309 löst das Problem, dass die Produktsuche nach Attributen in den Admin-Rastern langsam ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3 installiert ist. Die Patch-ID lautet MDVA-36309. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Produktsuche nach Attributen ist in den Admin-Rastern langsam.

<u>Schritte zur Reproduktion</u>:

Führen Sie die Suche in verschiedenen Admin-Rastern mit verschiedenen Typen durchsuchbarer Attribute durch.

<u>Erwartete Ergebnisse</u>:

Die Suche wird in angemessener Zeit durchgeführt.

<u>Tatsächliche Ergebnisse</u>:

Die Suche dauert sehr lange.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Überprüfen Sie mit dem Quality Patches Tool, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
