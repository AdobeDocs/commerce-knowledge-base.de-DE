---
title: "ACSD-47497: missing ACL for Store / Configuration / Services [!UICONTROL OAuth]"
description: Wenden Sie den Patch ACSD-47497 an, um das Adobe Commerce-Problem zu beheben, wenn Berechtigungen für eine bestimmte Rolle festgelegt sind, und Sie können den Zugriff auf den Konfigurationsabschnitt nicht definieren.
exl-id: c13fd541-1379-4893-9190-9da1422b2b99
feature: Configuration, Identity Management, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-47497: fehlende ACL für Store/Konfiguration/Dienste [!UICONTROL OAuth]

Der Patch ACSD-47497 behebt das Problem, bei dem die Registerkarte **[!UICONTROL Services]** im Abschnitt **[!UICONTROL Configuration]** im Adobe Commerce Admin nicht sichtbar ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23 installiert ist. Die Patch-ID ist ACSD-47497. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn Berechtigungen für eine bestimmte Rolle festgelegt werden, können Sie den Zugriff auf **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]** nicht definieren.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei Adobe Commerce Admin an. Gehen Sie zu **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]**.
1. Wählen Sie in der Rolle &quot;Administratoren&quot;den Wert &quot;**[!UICONTROL Role Resources]**&quot;, legen Sie unter &quot;**[!UICONTROL Roles Resources]**&quot;den Wert &quot;_Benutzerdefiniert_&quot;fest und aktivieren Sie dann alle Kontrollkästchen. **[!UICONTROL Resource Access]** Wählen Sie **[!UICONTROL Save Role]** aus.
1. Wählen Sie **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** aus. Der Konfigurationsabschnitt **[!UICONTROL OAuth]** ist nicht verfügbar.

<u>Erwartete Ergebnisse</u>:

In **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]** ist der Konfigurationsabschnitt sichtbar.

<u>Tatsächliche Ergebnisse</u>:

In **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]** fehlt der Konfigurationsabschnitt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
