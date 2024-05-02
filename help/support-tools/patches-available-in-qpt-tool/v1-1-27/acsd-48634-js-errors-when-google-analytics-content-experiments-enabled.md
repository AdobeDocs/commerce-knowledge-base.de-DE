---
title: '"ACSD-48634: [!DNL JS] Fehler bei [!DNL Google Analytics Content Experiments] enabled'''
description: Wenden Sie den Patch ACSD-48634 an, um ihn zu beheben. [!DNL JS] Fehler bei [!DNL staging] Seite aktualisieren, wenn [!DNL Google Analytics Content Experiments] aktiviert ist.
exl-id: 4a9f201d-eaf0-4e43-a1a1-0a9ffb0a2ead
feature: Catalog Management, Categories, Console, Page Content
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-48634: [!DNL JS] Fehler bei [!DNL Google Analytics Content Experiments] enabled

Die Patch-Fehlerbehebungen ACSD-48634 [!DNL JS] Fehler bei [!DNL staging] Seite aktualisieren, wenn [!DNL Google Analytics Content Experiments] aktiviert ist. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 ist installiert. Die Patch-ID lautet ACSD-48634. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

[!DNL JS] Fehler auftreten, wenn [!DNL staging] Seite aktualisieren, wenn [!DNL Google Analytics Content Experiments] aktiviert ist.

<u>Zu reproduzierende Schritte</u>:

1. In **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**, erstellen Sie eine zusätzliche Website, einen zusätzlichen Speicher und **[!UICONTROL Store View]**. Stellen Sie sicher, dass **[!UICONTROL Store View]** is *[!UICONTROL Enabled]*.
1. Konfigurieren **[!DNL Configure Google Analytics]** durch **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]**:
   * Für **[!DNL Main]** sowie zusätzliche Websites [!DNL scope]:
      * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**: *[!UICONTROL Google Tag Manager]*
      * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Container Id]**: *[!UICONTROL (GTM container ID)]*
      * **[!DNL Uncheck]** *[!UICONTROL Use Default]* für andere Felder, ändern Sie sie jedoch nicht.
   * Für **[!DNL Default Config]** [!DNL scope]:
      * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**: *[!UICONTROL Universal Analytics]*
      * **[!UICONTROL Account Number]**: *[!UICONTROL (Universal Analytics account number)]*
      * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
1. Deaktivieren **[!DNL Configure Google Analytics]** on **[!DNL Default Config]** [!DNL scope] durch Änderung **[!UICONTROL Enable]** von *[!UICONTROL Yes]* nach *[!UICONTROL No]*. Achten Sie darauf, nichts anderes zu ändern!
1. Navigieren Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
1. Erstellen und Bearbeiten beliebiger **[!UICONTROL category]** und fügen Sie eine geplante Aktualisierung hinzu:
   * Jeder Name, jedes Anfangsdatum in der Zukunft, jedes Enddatum in der Zukunft und jede Änderung in **[!UICONTROL category]** ([!UICONTROL For Example]: *[!UICONTROL disable category]*).
1. Speichern Sie die Aktualisierung und überprüfen Sie die [!DNL browser developer console] für Fehler.

<u>Erwartete Ergebnisse</u>:

Nein [!DNL JS] Fehler und Änderungen der [!DNL staging] Die Aktualisierung wurde erfolgreich gespeichert.

<u>Tatsächliche Ergebnisse</u>:

[!DNL JS] Fehler werden in der Konsole angezeigt, das Formular ist fehlerhaft und die [!DNL spinner] wird nach dem Speichern nie deaktiviert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
