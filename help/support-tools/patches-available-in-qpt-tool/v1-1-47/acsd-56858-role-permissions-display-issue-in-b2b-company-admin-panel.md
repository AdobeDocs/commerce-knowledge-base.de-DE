---
title: 'ACSD-56858: Diskrepanz bei Rollenberechtigungen in B2B-Unternehmens-Admin'
description: Wenden Sie den Patch ACSD-56858 an, um das Adobe Commerce-Problem zu beheben, bei dem Rollenberechtigungen für einen eingeschränkten Unternehmensadministrator in der B2B-Umgebung falsch angezeigt werden.
feature: Companies, B2B, Roles/Permissions
role: Admin, Developer
exl-id: d446f815-78bf-42ec-bc2b-a5934b15b416
source-git-commit: 4bf5deb1115705560acc8410441219943329c1a4
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-56858: Diskrepanz bei Rollenberechtigungen in B2B-Unternehmens-Admin

Mit dem Patch ACSD-56858 wird das Problem behoben, dass Rollenberechtigungen für einen eingeschränkten Unternehmensadministrator in der B2B-Umgebung falsch angezeigt werden. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.47 installiert ist. Die Patch-ID ist ACSD-56858. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Rollenberechtigungen für einen eingeschränkten Unternehmensadministrator in der B2B-Umgebung werden falsch angezeigt.

<u>Schritte zur Reproduktion</u>:

1. Beginnen Sie mit der Einrichtung einer Firma, indem Sie einen Unternehmensadministrator und Firmenbenutzer hinzufügen.
1. Melden Sie sich als Unternehmensadministrator an der Storefront an und erstellen Sie verschiedene Rollen für verschiedene Benutzer.
1. Weisen Sie diese Rollen nach Bedarf zu, z. B. indem Sie den Zugriff für einige Aufgaben einschränken und gleichzeitig anderen Benutzern vollständigen Zugriff gewähren.
1. Weisen Sie diese Rollen einem anderen Benutzer als dem Unternehmensadministrator mit vollem Zugriff zu.
1. Melden Sie sich bei einem Benutzer an, der kein Unternehmensadministrator ist, z. B. „company_manager“.
1. Navigieren Sie zu **[!UICONTROL Roles and permission]** und bearbeiten Sie die Rolle.
1. Beachten Sie, dass die angezeigten Berechtigungen nicht mit den in der Unternehmensdatenbank für diese Rollen-ID festgelegten Berechtigungen übereinstimmen.

<u>Erwartete Ergebnisse</u>:

Die Rollen und Berechtigungen werden für Benutzende ohne Unternehmensadministrator korrekt angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Die Rollen werden für den Benutzer, der kein Unternehmensadministrator ist, gemäß den Datenbankdatensätzen in der Berechtigungstabelle nicht korrekt angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
