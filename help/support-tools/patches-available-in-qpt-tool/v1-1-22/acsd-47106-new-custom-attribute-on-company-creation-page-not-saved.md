---
title: 'ACSD-47106: Neues benutzerdefiniertes Attribut auf der Seite „Unternehmenserstellung“ nicht gespeichert'
description: Wenden Sie den Patch ACSD-47106 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Wert nicht in einem neuen benutzerdefinierten Attribut auf einer Unternehmenserstellungsseite gespeichert werden kann.
exl-id: 941d6d8f-36eb-4b50-980f-e4afe6bf33df
feature: Attributes, B2B, Companies
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-47106: Neues benutzerdefiniertes Attribut auf der Seite „Unternehmenserstellung“ nicht gespeichert

Mit dem Patch ACSD-47106 wird das Problem behoben, dass ein Wert auf einer Unternehmenserstellungsseite nicht in einem neuen benutzerdefinierten Attribut gespeichert werden kann. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.22 installiert ist. Die Patch-ID ist ACSD-47106. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Ein Wert kann nicht in einem neuen benutzerdefinierten Attribut auf einer Unternehmenserstellungsseite gespeichert werden.

<u>Voraussetzungen</u>:

* B2B-Module werden installiert.

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie zu Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Customer]** > **[!UICONTROL Add New Attribute]**.
1. Neues Attribut erstellen: _Test 01_.
1. Gehen Sie zu Commerce Admin > **[!UICONTROL Customers]** > **[!UICONTROL Companies]** und erstellen Sie eine neue Firma mit allen erforderlichen Details.
1. Versuchen Sie, dem benutzerdefinierten Attribut einen Wert hinzuzufügen _Test 01_.
1. Versuchen Sie, den Wert des benutzerdefinierten Attributs zu aktualisieren _Test 01_.

<u>Erwartete Ergebnisse</u>:

Änderungen werden gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Änderungen werden nicht gespeichert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
