---
title: 'ACSD-48234: Falsche Anzahl der Kategorieelemente im Katalogsuchergebnis, wenn aktiviert[!UICONTROL Display Out of Stock Products]'
description: Wenden Sie den Patch ACSD-48234 an, um das Adobe Commerce-Problem zu beheben, bei dem das Katalogsuchergebnis eine falsche Anzahl von Kategorieelementen anzeigt, wenn die Option [!UICONTROL Display Out of Stock Products] aktiviert ist.
exl-id: 8e70fe73-d550-4e11-b25e-84955e136d12
feature: Admin Workspace, Categories, Catalog Management, Orders, Products, Search
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-48234: Das Ergebnis der Katalogsuche zeigt eine falsche Anzahl von Kategorieelementen **[!UICONTROL Display Out of Stock Products]** aktiviert an

Der Patch ACSD-48234 löst das Problem, dass das Katalogsuchergebnis eine falsche Anzahl von Kategorieelementen anzeigt, wenn die Option **[!UICONTROL Display Out of Stock Products]** aktiviert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 installiert ist. Die Patch-ID ist ACSD-48234. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.


## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.5-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Ergebnis der Katalogsuche zeigt eine falsche Anzahl von Kategorieelementen an, wenn die Option **[!UICONTROL Display Out of Stock Products]** aktiviert ist.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** und öffnen Sie **[!UICONTROL color]** Attribut .
1. Fügen Sie zwei Optionen hinzu, z. B. orange und grün. Speichern Sie das Attribut.
1. Wechseln Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]** und fügen Sie dem **[!UICONTROL Default]** Attributsatz das Attribut **[!UICONTROL color]** hinzu.
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** und setzen Sie **[!UICONTROL Display Out of Stock Products]** auf _Ja_.
1. Kategorie „cat1“ erstellen.
1. Erstellen Sie zwei Produkte:
   1. Name: prod1, Farbe: orange, Kategorien: cat1.
   1. Name: prod2, Farbe: grün, Kategorien: cat1.
1. Öffnen Sie die Kategorie „cat1“ in der Storefront.
1. Wählen Sie die orangefarbene Farbe in der mehrschichtigen Navigation aus.

<u>Erwartete Ergebnisse</u>:

Es wird nur das Produkt prod1 angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Es werden sowohl prod1- als auch prod2-Produkte angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
