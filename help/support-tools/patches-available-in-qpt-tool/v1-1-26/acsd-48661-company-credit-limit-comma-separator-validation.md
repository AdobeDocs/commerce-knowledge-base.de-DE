---
title: "ACSD-48661: Validierungsproblem für das Unternehmenskreditlimit für ein gemeinsames Trennzeichen"
description: Wenden Sie den Patch ACSD-48661 an, um das Adobe Commerce-Problem zu beheben. Wenn die Firmenkreditbeschränkung größer als 999 ist, verhindert das Kommatrennzeichen die Speicherung des Unternehmens aufgrund eines Validierungsfehlers.
exl-id: 85c5a93f-76c5-439b-adcc-511f8473f302
feature: Admin Workspace, B2B, Companies, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# ACSD-48661: Problem mit der Validierung eines Unternehmenskreditlimits für ein gemeinsames Trennzeichen

Der Patch ACSD-48661 behebt das Problem, bei dem das Firmenkreditlimit größer als 999 ist, das Kommatrennzeichen die Speicherung des Unternehmens aufgrund eines Validierungsfehlers verhindert. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 installiert ist. Die Patch-ID ist ACSD-48661. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn das Firmenkreditlimit größer als 999 ist, verhindert das Kommatrennzeichen, dass das Unternehmen aufgrund eines Validierungsfehlers gespeichert wird.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie die Funktion &quot;Unternehmen&quot;unter **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Erstellen Sie ein Unternehmen und fügen Sie unter dem Wert **[!UICONTROL Company Credit]** Registerkarte.
1. Speichern Sie das Unternehmen.
1. Bearbeiten Sie das Unternehmen und versuchen Sie erneut, es zu speichern.

<u>Erwartete Ergebnisse</u>:

Sie können das Unternehmen speichern, ohne die Kreditgrenze festzulegen. Komma wird nicht für Eingabefelder für die Beträge und Preise unterstützt.

<u>Tatsächliche Ergebnisse</u>:

Sie können das Unternehmen aufgrund eines Validierungsfehlers im *[!UICONTROL Credit Limit]* -Feld. Adobe Commerce fügt automatisch Komma-Trennzeichen für Kreditbeschränkungen hinzu, auch wenn die Variable [!UICONTROL Credit Limit] -Feld akzeptiert keine Kommas.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
