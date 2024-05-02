---
title: '"ACSD-47027: langsame Abfrage B2B [!UICONTROL CompanyRole] [!DNL GraphQL] update'''
description: Wenden Sie den Patch ACSD-47027 an, um das Adobe Commerce-Problem zu beheben, bei dem eine langsame Abfrage B2B vorhanden ist. [!UICONTROL CompanyRole] [!DNL GraphQL] aktualisieren.
exl-id: 478ae16b-7722-4469-8f8a-a38820e61ae4
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-47027: langsame Abfrage B2B [!UICONTROL CompanyRole] [!DNL GraphQL] update

Der Patch ACSD-47027 behebt das Problem, bei dem die langsame Abfrage B2B [!UICONTROL CompanyRole] [!DNL GraphQL] Aktualisierung funktioniert nicht erwartungsgemäß. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23 installiert ist. Die Patch-ID ist ACSD-47027. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die langsame Abfrage B2B [!UICONTROL CompanyRole] [!DNL GraphQL] Aktualisierung funktioniert nicht erwartungsgemäß.

<u>Voraussetzungen</u>:

Installieren Sie das B2B-Modul.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie im Adobe Commerce-Admin zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configurations]** > **[!UICONTROL B2B Features]** und **[!UICONTROL Enable Company]** nach _Ja_.
1. Gehen Sie zum Frontend und erstellen Sie ein Unternehmen.
1. Nachdem Sie sich als Unternehmensbenutzer angemeldet haben, gehen Sie zu **[!UICONTROL My Account]** > **[!UICONTROL Roles and Permissions]** und eine neue Rolle hinzufügen.
1. Aktivieren [!UICONTROL dev] Abfrageprotokoll mit `bin/magento dev:que:enab`.
1. Senden Sie jetzt Folgendes [!DNL GraphQL] request (id ist die [!UICONTROL base64] kodierte Rollen-ID):

   <pre><code>
   mutation {
   updateCompanyRole(
      input: {
         id: "Mg=="
         permissions: [
         "Magento_Company::view"
         "Magento_Company::view_account"
         "Magento_Company::user_management"
         "Magento_Company::roles_view"
        ]
      }
    ) {
      role {
         id

         name

         permissions {
         id

         text

         children {
            id

            text

            children {
               id

               text
             }
           }
         }
       }
     }
   }
   </code></pre>

1. Überprüfen Sie das Abfrageprotokoll.
1. Sie können sehen, dass die obige Abfrage ausgeführt wird. Diese Abfrage wird in `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources`.

<u>Erwartete Ergebnisse</u>:

Die `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` muss optimiert werden, um zu vermeiden, dass alle in der Variablen **[!UICONTROL company_permissions]** DB-Tabelle.

<u>Tatsächliche Ergebnisse</u>:

Adobe Commerce führt eine Abfrage ohne Filter aus. Bei einer großen Anzahl von Datensätzen dauert es sehr lange, bis Adobe Commerce die Datenerfassung vorbereitet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation. 

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
