---
title: '"ACSD-54324: GraphQL-Anfrage "Requisition_lists"berücksichtigt keine Paginierungseinstellungen."'
description: Wenden Sie den Patch ACSD-54324 an, um das Adobe Commerce-Problem zu beheben, bei dem die GraphQL-Anfrage "Requisition_lists"keine Paginierungseinstellungen berücksichtigt und alle Ergebnisse zurückgibt.
feature: B2B, Customers, GraphQL
role: Admin, Developer
exl-id: 85297eae-bedf-4624-9758-0b68452d131b
source-git-commit: b5894687704594a4e751c230246bdf167b1b6402
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# ACSD-54324: GraphQL `requisition_lists` -Anfrage berücksichtigt keine Paginierungseinstellungen

Der Patch ACSD-54324 behebt das Problem, bei dem der GraphQL `requisition_lists` -Anfrage berücksichtigt keine Paginierungseinstellungen und gibt alle Ergebnisse zurück. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.41 installiert ist. Die Patch-ID ist ACSD-54324. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die GraphQL `requisition_lists` -Anfrage berücksichtigt keine Paginierungseinstellungen und gibt alle Ergebnisse zurück.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei Admin an und navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

   * Satz *[!UICONTROL Enable Requisition List]* nach *Ja*.

1. Melden Sie sich beim Frontend an und gehen Sie zu **[!UICONTROL My Requisition Lists]** über das obere Menü oder von **[!UICONTROL My Account]** und erstellen Sie mehrere Anforderungen (Beispiel: 7).
1. Führen Sie nach dem Generieren eines Kunden-Tokens den folgenden GraphQL aus `requisition_lists` Abfrage für den Kunden.

   * Stellen Sie sicher, dass die Seitengröße kleiner ist als die Gesamtzahl der von Ihnen erstellten Anforderungslisten (Beispiel: 4)

   ```
   {
   customer {
   requisition_lists(pageSize: 4, currentPage: 1) {
   items
   
   { uid name description updated_at items_count }
   total_count
   }
   }
   }
   ```

1. Beachten Sie, dass der Wert der `total_count` zeigt 7 an, wann 4 angezeigt werden sollte.

   Die Anzahl der Elemente zeigt auch 7 an, wenn es mit der *Seitengröße*.

<u>Erwartete Ergebnisse</u>:

* Die Zahl wird als *Seitengröße* zurückgegeben unter `total_count` und nicht die Gesamtzahl der Datensätze.
* Die Anzahl der Elemente entspricht der *Seitengröße*.

<u>Tatsächliche Ergebnisse</u>:

Die Gesamtzahl der Datensätze wird zurückgegeben unter `total_count`, auch wenn *Seitengröße* erwähnt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
