---
title: "ACSD-54983: Benutzer-UID des Unternehmens mit GraphQL ist bei inaktiven Benutzern nicht verfügbar"
description: Wenden Sie den Patch ACSD-54983 an, um das Adobe Commerce-Problem zu beheben, bei dem es nicht möglich ist, die Benutzer-UID des Unternehmens mit GraphQL-Anfrage abzurufen, wenn der Benutzerstatus auf "Inaktiv"gesetzt ist.
feature: GraphQL
role: Admin, Developer
exl-id: 57e7b9ca-3421-4b50-86b4-abdf1b3d79d1
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# ACSD-54983: Benutzer-UID des Unternehmens mit GraphQL ist bei inaktiven Benutzern nicht verfügbar

Der Patch ACSD-54983 behebt das Problem, bei dem es nicht möglich ist, die Benutzer-UID des Unternehmens mit der GraphQL-Anfrage abzurufen, wenn der Benutzerstatus auf &quot;Inaktiv&quot;gesetzt ist. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 ist installiert. Die Patch-ID ist ACSD-54983. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Benutzer-UID des Unternehmens kann nicht mit der GraphQL-Anfrage abgerufen werden, wenn der Benutzerstatus auf &quot;Inaktiv&quot;festgelegt ist.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Unternehmen mit einem Administrator-Benutzer. Beispiel: company@test.com.
1. Erstellen Sie einen neuen Kunden.
1. Weisen Sie den neuen Kunden einem Unternehmen zu.
1. Abrufen einer **[!UICONTROL company admin token]**.
1. Verwenden der **[!UICONTROL company admin token]**, rufen Sie die Unternehmensstruktur ab. Siehe [Unternehmensstruktur zurückgeben](https://developer.adobe.com/commerce/webapi/graphql/schema/b2b/company/queries/company/#return-the-company-structure) in unserer Entwicklerdokumentation.
1. Die Antwort enthält nur *AKTIV* -Kunden mit ihren IDs.
1. Aktualisieren Sie den Unternehmensbenutzer auf *INAKTIV*.
1. Rufen Sie die Unternehmensstruktur erneut ab.

<u>Erwartete Ergebnisse</u>:

Es ist möglich, die Benutzer-UID des Unternehmens abzurufen, wenn der Status auf &quot;Inaktiv&quot;festgelegt ist.

<u>Tatsächliche Ergebnisse</u>:

Die inaktiven Kunden sind nicht in der Liste enthalten. Die Benutzer-UID des Unternehmens kann nicht abgerufen werden, wenn der Status auf &quot;Inaktiv&quot;festgelegt ist.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
