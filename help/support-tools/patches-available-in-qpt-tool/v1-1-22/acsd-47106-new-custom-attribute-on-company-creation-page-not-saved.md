---
title: "ACSD-47106: Neues benutzerdefiniertes Attribut auf der Seite zur Unternehmenserstellung nicht gespeichert"
description: Wenden Sie den Patch ACSD-47106 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Wert nicht in einem neuen benutzerdefinierten Attribut auf einer Seite zur Unternehmenserstellung gespeichert werden kann.
exl-id: 941d6d8f-36eb-4b50-980f-e4afe6bf33df
feature: Attributes, B2B, Companies
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-47106: neues benutzerdefiniertes Attribut auf der Seite zur Unternehmenserstellung nicht gespeichert

Der Patch ACSD-47106 behebt das Problem, dass ein Wert nicht in einem neuen benutzerdefinierten Attribut auf einer Seite zur Unternehmenserstellung gespeichert werden kann. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.22 installiert ist. Die Patch-ID ist ACSD-47106. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Ein Wert kann nicht in einem neuen benutzerdefinierten Attribut auf einer Seite zur Unternehmenserstellung gespeichert werden.

<u>Voraussetzungen</u>:

* B2B-Module sind installiert.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Customer]** > **[!UICONTROL Add New Attribute]**.
1. Erstellen Sie ein neues Attribut: _Test 01_.
1. Gehen Sie zu Commerce Admin > **[!UICONTROL Customers]** > **[!UICONTROL Companies]** > und erstellen Sie ein neues Unternehmen mit allen erforderlichen Details.
1. Versuchen Sie, dem benutzerdefinierten Attribut _Test 01_ einen Wert hinzuzufügen.
1. Versuchen Sie, den Wert des benutzerdefinierten Attributs _Test 01_ zu aktualisieren.

<u>Erwartete Ergebnisse</u>:

Änderungen werden gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Änderungen werden nicht gespeichert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
