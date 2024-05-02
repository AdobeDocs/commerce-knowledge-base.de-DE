---
title: '"ACSD-56515: Admin mit Berechtigungen auf Website-Ebene kann nicht bearbeiten [!UICONTROL Dynamic Block]'''
description: Wenden Sie den Patch ACSD-56515 an, um das Adobe Commerce-Problem zu beheben, bei dem der Administrator mit Berechtigungen auf Website-Ebene die [!UICONTROL Dynamic Block].
feature: Roles/Permissions, Admin Workspace
role: Admin, Developer
exl-id: 5aa6b11e-b467-4076-ad36-162966cbf6df
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-56515: Admin mit Berechtigungen auf Website-Ebene kann nicht bearbeiten [!UICONTROL Dynamic Block]

Der Patch ACSD-56515 behebt das Problem, dass der Administrator mit Berechtigungen auf Website-Ebene die [!UICONTROL Dynamic Block]. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 ist installiert. Die Patch-ID ist ACSD-56515. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Administrator mit Berechtigungen auf Website-Ebene kann die [!UICONTROL Dynamic Block].

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine sekundäre Website mit Store und Store-Überprüfung.
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]** und erstellen Sie eine Benutzerrolle, die auf den sekundären Website-Bereich beschränkt ist und alle verfügbaren Ressourcen enthält.
1. Erstellen Sie einen Admin-Benutzer mit der oben erstellten Rolle.
1. Melden Sie sich mit dem eingeschränkten Administratorbenutzer an und erstellen Sie eine [!UICONTROL Dynamic Block].

<u>Erwartete Ergebnisse</u>:

Der Admin-Benutzer mit Einschränkungen für die Website kann eine [!UICONTROL Dynamic Block].

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten den folgenden Fehler: *Weitere Berechtigungen zum Anzeigen dieses Elements sind erforderlich*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
