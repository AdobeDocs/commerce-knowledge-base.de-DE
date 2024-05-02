---
title: "ACSD-56858: Diskrepanz bei Rollenberechtigungen in B2B-Unternehmensadministratoren"
description: Wenden Sie den Patch ACSD-56858 an, um das Adobe Commerce-Problem zu beheben, bei dem Rollenberechtigungen fälschlicherweise für einen eingeschränkten Unternehmensadministrator in der B2B-Umgebung angezeigt werden.
feature: Companies, B2B, Roles/Permissions
role: Admin, Developer
exl-id: d446f815-78bf-42ec-bc2b-a5934b15b416
source-git-commit: 4bf5deb1115705560acc8410441219943329c1a4
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-56858: Diskrepanz bei Rollenberechtigungen in B2B-Unternehmensadministratoren

Der Patch ACSD-56858 behebt das Problem, dass Rollenberechtigungen fälschlicherweise für einen eingeschränkten Unternehmensadministrator in der B2B-Umgebung angezeigt werden. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.47 ist installiert. Die Patch-ID ist ACSD-56858. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Rollenberechtigungen für einen eingeschränkten Unternehmensadministrator in der B2B-Umgebung werden ungenau angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Beginnen Sie mit der Einrichtung eines Unternehmens, dem Hinzufügen eines Unternehmens-Administrators und von Benutzern des Unternehmens.
1. Melden Sie sich als Unternehmensadministrator an der Storefront an und erstellen Sie verschiedene Rollen für verschiedene Benutzer.
1. Weisen Sie diese Rollen nach Bedarf zu, z. B. den Zugriff auf einige Aufgaben zu begrenzen und gleichzeitig den uneingeschränkten Zugriff für andere zu.
1. Weisen Sie diese Rollen einem anderen Benutzer als dem Unternehmensadministrator vollen Zugriff zu.
1. Melden Sie sich bei einem Benutzer an, der kein Unternehmens-Admin ist, z. B. bei einem company_manager.
1. Navigieren Sie zu **[!UICONTROL Roles and permission]** und bearbeiten Sie die Rolle.
1. Beachten Sie, dass die angezeigten Berechtigungen nicht mit den in der Datenbank des Unternehmens festgelegten Berechtigungen für diese Rollen-ID übereinstimmen.

<u>Erwartete Ergebnisse</u>:

Die Rollen und Berechtigungen werden für Benutzer ohne Unternehmens-Admin-Berechtigung korrekt angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Die Rollen werden für Benutzer ohne firmeneigene Administratorrechte nicht korrekt angezeigt, wie in den Datenbankdatensätzen in der Berechtigungstabelle angegeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
