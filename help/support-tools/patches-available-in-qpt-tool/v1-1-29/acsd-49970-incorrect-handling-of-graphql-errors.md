---
title: "ACSD-49970: Falsche Handhabung von GraphQL-Fehlern"
description: Wenden Sie den Patch ACSD-49970 an, um das Adobe Commerce-Problem zu beheben, bei dem GraphQL-Fehler falsch behandelt werden, wenn [!UICONTROL New Relic Reporting] aktiviert ist.
exl-id: 70acade5-02a5-4769-86e2-5c566b2af709
feature: GraphQL, Observability
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-49970: Falsche Handhabung von GraphQL-Fehlern

Der Patch ACSD-49970 behebt das Problem, bei dem GraphQL-Fehler falsch behandelt werden, wenn *[!UICONTROL New Relic Reporting]* aktiviert ist. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 ist installiert. Die Patch-ID ist ACSD-49970. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

`GraphQLOperationNames` -Schlüssel nicht ordnungsgemäß verarbeitet werden, unabhängig davon, ob die `logDataHelper` enthält diesen Schlüssel oder nicht.

<u>Zu reproduzierende Schritte</u>:

1. Ausführen `bin/magento deploy:mode:set developer`.
1. Melden Sie sich beim Administrator an.
1. Aktivieren **[!UICONTROL New Relic Integration]** von **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL New Relic Reporting]**
(Hinweis: Selbst wenn ein Fehler angezeigt wird, der besagt, dass die Variable [!DNL New Relic] -Erweiterung nicht verfügbar ist, wird die Konfiguration gespeichert).
1. Ausführen *GraphQL* Mutation zu `http://yourMagentoDomain/graphql` aus dem *[!DNL Altair]* Client oder einem anderen Client oder über cURL.

   ```GraphQL
   mutation {
       createEmptyCart
   }
   ```

   (Hinweis: Legen Sie die **[!UICONTROL Header]** nach [!UICONTROL Content-Currency:CA] vor der Ausführung).

   ```cURL
   curl --location 'http://yourMagentoDomain/graphql' \--header 'Content-Currency: CA' \--header 'Content-Type: application/json' \--header 'Cookie: PHPSESSID=b5147f63fe5014ea523f262946; private_content_version=8d53dfda210a6e9bc46f4e4a01ffd6c5' \--data '{"query":"mutation {\r\n  createEmptyCart\r\n}","variables":{}}'
   ```

<u>Erwartete Ergebnisse</u>:

Es gibt keine *500 Ausnahme* in Protokollen, `GraphQLOperationNames` -Schlüssel korrekt verarbeitet werden.

<u>Tatsächliche Ergebnisse</u>:

Es gibt eine *500 Ausnahme* in Protokollen, `GraphQLOperationNames` -Schlüssel nicht korrekt verarbeitet werden.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
