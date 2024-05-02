---
title: 'ACSD-54026: Falsche Fehlermeldung für updateCompanyRole GraphQL-Anfrage'
description: Wenden Sie den Patch ACSD-54026 an, um das Adobe Commerce-Problem zu beheben, bei dem eine falsche Fehlermeldung für eine GraphQL-Anfrage updateCompanyRole für einen nicht autorisierten Benutzer vorliegt.
feature: Roles/Permissions
role: Admin, Developer
exl-id: c18a8815-975a-499d-a372-8635d89aa673
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-54026: Falsche Fehlermeldung für `updateCompanyRole` GraphQL-Anfrage

Der Patch ACSD-54026 behebt das Problem, dass eine falsche Fehlermeldung für eine `updateCompanyRole` GraphQL-Anfrage an einen nicht autorisierten Benutzer. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.39 ist installiert. Die Patch-ID ist ACSD-54026. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Abrufen einer falschen Fehlermeldung für eine `updateCompanyRole` GraphQL-Anfrage an einen nicht autorisierten Benutzer.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie das B2B-Unternehmen in der Konfiguration.
1. Erstellen Sie ein Unternehmen.
1. Senden Sie eine `updateCompanyRole` GraphQL-Anfrage ohne Übergabe eines Trägertokens oder mit einem ungültigen Bearer-Token.
1. Beobachten Sie die Fehlermeldung in der GraphQL-Antwort.

<u>Erwartete Ergebnisse</u>:

Sie erhalten die folgende Fehlermeldung: *Der aktuelle Kunde ist nicht autorisiert.*

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten die folgende Fehlermeldung: *Der Kunde ist kein Unternehmensbenutzer.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
