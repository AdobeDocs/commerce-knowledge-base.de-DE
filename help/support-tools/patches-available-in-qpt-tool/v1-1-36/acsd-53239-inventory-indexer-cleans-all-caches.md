---
title: 'ACSD-53239: Inventar-Indexer bereinigt alle Caches'
description: Wenden Sie den Patch ACSD-53239 an, um das Adobe Commerce-Problem zu beheben, bei dem der Inventar-Indexer alle Caches im [!UICONTROL Update on Schedule] bereinigt.
feature: GraphQL, Inventory, Catalog Management
role: Admin, Developer
exl-id: b8e68cf7-d326-4c9e-8749-d83113de2070
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# ACSD-53239: Der Inventar-Indexer bereinigt alle Caches im [!UICONTROL Update on Schedule]

Der Patch ACSD-53239 behebt das Problem, dass der Inventar-Indexer alle Caches im [!UICONTROL Update on Schedule] bereinigt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.36 installiert ist. Die Patch-ID ist ACSD-53239. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.5-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Inventar-Indexer bereinigt alle Caches im [!UICONTROL Update on Schedule].

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Catalog Products]** und wählen Sie etwa *1200* Produkte aus.
2. Aktualisieren Sie *[!UICONTROL Qty]* auf einen neuen Wert und klicken Sie auf **[!UICONTROL Save]**.
3. `bin/magento cron:run` sofort nach dem Speichern ausführen.
4. Führen Sie die folgende GraphQL-Abfrage aus:

   ```GraphQL
   {
     storeConfig {
     absolute_footer
     }
   }
   ```

<u>Erwartete Ergebnisse</u>

Die Abfrage wird innerhalb der üblichen Zeit verarbeitet.

<u>Tatsächliche Ergebnisse</u>

Die Abfrage wird ungewöhnlich langsam verarbeitet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
