---
title: 'ACSD-49839: Freigegebene Katalogpreise und -struktur geben einen Fehler aus'
description: Wenden Sie den Patch ACSD-49839 an, um das Adobe Commerce-Problem zu beheben, bei dem die freigegebene Katalogpreisstruktur einen Fehler in der Admin auslöst, wenn Produkte Einzel- oder Doppelanführungszeichen in der SKU haben.
exl-id: 4c477ae8-602b-452e-83f0-b72a29547ef9
feature: Admin Workspace, Catalog Management, Categories
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-49839: Freigegebene Katalogpreise und -struktur geben einen Fehler aus

Der Patch ACSD-49839 behebt das Problem, dass die freigegebene Katalogpreisstruktur einen Fehler in der Admin auslöst, wenn Produkte Einfach- oder Doppelanführungszeichen in der SKU haben. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 installiert ist. Die Patch-ID ist ACSD-49839. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die freigegebene Katalogpreisstruktur gibt einen Fehler in der Admin aus, wenn Produkte einfache oder doppelte Anführungszeichen in der SKU haben.

<u>Schritte zur Reproduktion</u>:

1. Legen Sie einige Produkt-SKUs mit einem Sonderzeichen fest, d. h. doppelte Anführungszeichen wie:
   *[Produkt„12, Produkt„14, Produkt„15]*.
1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalog]** > **[!UICONTROL Add Shared Catalog]** (z. B. *[Freigegebenen Katalog testen]*).
1. Alle **[!UICONTROL Products and Categories]** zuweisen > **[!UICONTROL Generate Catalog]** > **[!UICONTROL Save]**.
1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalog]** > **[!UICONTROL Test Shared Catalog]** > **[!UICONTROL Action]** > **[!UICONTROL Set Pricing and Structure]**.
1. Markieren Sie *[!UICONTROL Root Catalog]*, um alle Kategorien und Produkte auszuwählen.
1. Beobachten Sie die AJAX-Anfragen im Netzwerkbereich.

<u>Erwartete Ergebnisse</u>:

Gemeinsame Katalogpreise und -strukturen lösen keinen Fehler in der Admin aus, wenn Produkte einfache oder doppelte Anführungszeichen in der SKU haben.

<u>Tatsächliche Ergebnisse</u>:

Gemeinsame Katalogpreise und -struktur lösen einen Fehler in der Admin-Liste aus, wenn Produkte einfache oder doppelte Anführungszeichen in der SKU haben.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
