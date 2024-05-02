---
title: '''[!DNL ACSD-47280]: Durch Deaktivieren des freigegebenen Katalogs werden falsche Produktsuchergebnisse angezeigt."'
description: Wenden Sie die [!DNL ACSD-47280] Patch zu korrigieren, das die korrekten Suchergebnisse anzeigt, wenn die Funktion des freigegebenen Katalogs deaktiviert ist.
exl-id: 98bbae42-fd68-4b54-823d-189d742cc35f
source-git-commit: 975f5b5c95ad488128a5dbb3488b8d54f7b73b59
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# [!DNL ACSD-47280]: Das Deaktivieren des freigegebenen Katalogs führt zu falschen Produktsuchergebnissen.

Die [!DNL ACSD-47280] Patch behebt die Anzeige der richtigen Suchergebnisse, wenn die [!DNL shared catalog] -Funktion deaktiviert ist. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.22 installiert ist. Die [!DNL patch ID] is [!DNL ACSD-47280]. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die [!DNL patch ID] als Suchbegriff, um den Patch zu finden.

## Problem

Deaktivieren [!DNL shared catalog] gibt falsche Produktsuchergebnisse zurück.

<u>Voraussetzungen</u>:

* [!DNL B2B] installierte Module

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine zweite Website.
1. Weisen Sie der zweiten Website ein Produkt zu.
1. Überprüfen Sie die Produkte auf der **zweite Website** using [!DNL GraphQL]:

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

1. Aktivieren **[!UICONTROL Shared Catalog]** standardmäßig [!DNL scope].
1. Die [!DNL GraphQL] -Anfrage zeigt keine Produkte für die zweite Website mehr an, was das richtige Ergebnis ist.
1. Navigieren Sie zu [!DNL scope] der zweiten Website und deaktivieren Sie **[!UICONTROL Company]**.

<u>Erwartete Ergebnisse</u>:

Die [!DNL GraphQL] -Anfrage sollte weiterhin Produkte für die zweite Website anzeigen.

<u>Tatsächliche Ergebnisse</u>:

Die [!DNL GraphQL] -Anfrage zeigt keine Produkte für die zweite Website an.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
