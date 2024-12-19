---
title: '[!DNL ACSD-47280]: Freigegebenen Katalog deaktivieren liefert falsche Produktsuchergebnisse'
description: Wenden Sie den  [!DNL ACSD-47280]  an, um zu beheben, dass die richtigen Suchergebnisse angezeigt werden, wenn die Funktion „Freigegebener Katalog“ deaktiviert ist.
exl-id: 98bbae42-fd68-4b54-823d-189d742cc35f
source-git-commit: 975f5b5c95ad488128a5dbb3488b8d54f7b73b59
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# [!DNL ACSD-47280]: Durch Deaktivieren des freigegebenen Katalogs erhalten Sie falsche Produktsuchergebnisse

Der [!DNL ACSD-47280] Patch behebt die Anzeige der richtigen Suchergebnisse, wenn die [!DNL shared catalog] deaktiviert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.22 installiert ist. Die [!DNL patch ID] ist [!DNL ACSD-47280]. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie den [!DNL patch ID] als Suchbegriff, um den Patch zu finden.

## Problem

Durch Deaktivieren von [!DNL shared catalog] erhalten Sie falsche Produktsuchergebnisse.

<u>Voraussetzungen</u>:

* Installierte [!DNL B2B]

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine zweite Website.
1. Weisen Sie der zweiten Website ein Produkt zu.
1. Überprüfen Sie die Produkte auf der **zweiten Website** mithilfe von [!DNL GraphQL]:

   ```GraphQL
   {
     products(search: "bag", pageSize: 2) {
       total_count
       items {
         name
         sku
       }
       page_info {
         page_size
         current_page
       }
     }
   }
   ```

1. Aktivieren Sie **[!UICONTROL Shared Catalog]** auf [!DNL scope].
1. Die [!DNL GraphQL] Anfrage zeigt keine Produkte mehr für die zweite Website an, was das richtige Ergebnis ist.
1. Gehen Sie zum [!DNL scope] der zweiten Website und deaktivieren Sie **[!UICONTROL Company]**.

<u>Erwartete Ergebnisse</u>:

Die [!DNL GraphQL] sollte weiterhin Produkte für die zweite Website enthalten.

<u>Tatsächliche Ergebnisse</u>:

Die [!DNL GraphQL] Anfrage zeigt keine Produkte für die zweite Website an.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
