---
title: "ACSD-49527: GraphQL-Unternehmensrollen zeigen die Paginierung nicht korrekt an."
description: Wenden Sie den Patch ACSD-49527 an, um das Adobe Commerce-Problem zu beheben, bei dem die GraphQL-Unternehmensrollen die Paginierung nicht korrekt anzeigen.
exl-id: e2d50081-8002-490e-9476-a19ba6623bda
feature: B2B, GraphQL, Companies, Roles/Permissions
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-49527: GraphQL-Unternehmensrollen zeigen die Paginierung nicht korrekt an

Der Patch ACSD-49527 behebt das Problem, dass die GraphQL-Unternehmensrollen die Paginierung nicht korrekt anzeigen. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 ist installiert. Die Patch-ID lautet ACSD-49527. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

GraphQL-Unternehmensrollen zeigen die Paginierung nicht richtig an.

<u>Zu reproduzierende Schritte</u>:

1. B2B-Unternehmen aktivieren.
1. Erstellen Sie auf der Storefront ein neues Unternehmen.
1. Erstellen Sie mindestens zwei neue Rollen für dieses Unternehmen, sodass es insgesamt drei Rollen gibt, da eine Rolle die Standardrolle ist.
1. GraphQL-Anforderung senden, um Rollen zu erhalten, die [!UICONTROL pageSize]2.

   ```GraphQL
   query {
       company {
           roles(pageSize: 2, currentPage: 1) {
               items {
                   name
               }
               total_count
               page_info {
                   total_pages
                   current_page
               }
           }
       }
   } 
   ```

1. Überprüfen Sie die GraphQL-Antwort.

<u>Erwartete Ergebnisse</u>:

`total_count: 3` und `total_pages: 2` werden in der GraphQL-Antwort zurückgegeben.

<u>Tatsächliche Ergebnisse</u>:

`total_count: 2` und `total_pages: 1` werden in der GraphQL-Antwort zurückgegeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
