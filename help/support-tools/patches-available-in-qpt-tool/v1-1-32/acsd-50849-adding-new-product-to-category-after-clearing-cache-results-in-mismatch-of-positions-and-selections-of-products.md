---
title: 'ACSD-50849: Das Hinzufügen eines neuen Produkts nach dem Löschen des Caches führt zu einer Nichtübereinstimmung'
description: Wenden Sie den Patch ACSD-50849 an, um das Adobe Commerce-Problem zu beheben, bei dem das Hinzufügen eines neuen Produkts zur Kategorie nach dem Löschen des Caches zu einer Diskrepanz der Positionen und Auswahlen der vorhandenen Produkte führt.
feature: Cache, Categories, Products
role: Admin
exl-id: 3c797bf4-45da-4500-8c06-8c1007249738
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-50849: Das Hinzufügen eines neuen Produkts nach dem Löschen des Caches führt zu einer Nichtübereinstimmung

Mit dem Patch ACSD-50849 wird das Problem behoben, dass das Hinzufügen eines neuen Produkts zur Kategorie nach dem Löschen des Cache zu einer Nichtübereinstimmung der Positionen und Auswahlen der vorhandenen Produkte führt. Dieser Patch ist verfügbar, wenn das [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) QPT 1.1.32 installiert ist. Die Patch-ID ist ACSD-50849. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn Sie der Kategorie nach dem Löschen des Caches ein neues Produkt hinzufügen, führt dies zu einer Diskrepanz bei den Positionen und Auswahlen der vorhandenen Produkte.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie zwei Produkte.
1. Weisen Sie einer Kategorie ein Produkt zu.
1. Öffnen Sie die Kategorie über den Administrator.
1. `bin/magento cache:flush` bereinigen.
1. Fügen Sie das zweite Produkt zur Kategorie hinzu.

<u>Erwartete Ergebnisse</u>:

Die vorhandenen Produkte, die der Kategorie zugewiesen sind, werden nicht automatisch entfernt.

<u>Tatsächliche Ergebnisse</u>:

Das erste (vorhandene) Produkt wird automatisch entfernt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
