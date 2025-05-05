---
title: 'ACSD-58790: Korrigiert die Pinch-to-Zoom-Funktion auf den Produktdetailseiten der Bilder in der mobilen Ansicht auf [!DNL Chrome]'
description: Mit ACSD-58790 wird das Adobe Commerce-Problem behoben, bei dem das Bild in der mobilen Ansicht auf  [!DNL Chrome]  nicht wie erwartet vergrößert wurde.
feature: Storefront
role: Admin, Developer
exl-id: 0985534c-49af-439a-8859-39222dedcf67
source-git-commit: a84c3d296deb49d419be78f454696177a974d923
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-58790: Korrigiert die Pinch-to-Zoom-Funktion auf den Produktdetailseiten-Bildern in der Mobilansicht auf [!DNL Chrome]

Mit dem Patch „ACSD-58790“ wird das Adobe Commerce-Problem behoben, bei dem das Bild in der mobilen Ansicht auf [!DNL Chrome] nicht wie erwartet vergrößert wurde. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 installiert ist. Die Patch-ID ist ACSD-58790. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Korrigiert die Pinch-to-Zoom-Funktion auf den Produktdetailseiten-Bildern in der Mobile-Ansicht auf [!DNL Chrome].

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein Produkt mit einem Bild.
1. Öffnen Sie das Produkt in einem [!DNL Chrome].
1. Klicken Sie auf das Bild und stellen Sie sicher, dass das Bild beim Doppelklicken vergrößert wird.
1. Wechseln Sie mithilfe der [!DNL Chrome] Entwickler-Tools zur mobilen Ansicht.
1. Klicken Sie auf das Bild.
1. Doppeltippen.

<u>Erwartete Ergebnisse</u>:

Das Bild wird beim Doppelklicken vergrößert.

<u>Tatsächliche Ergebnisse</u>:

Das Bild wird beim Doppelklicken nicht vergrößert. Dieses Problem tritt nur bei [!DNL Chrome] in der Mobilansicht auf, da die Zoom-Funktion in [!DNL Firefox] wie erwartet funktioniert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
