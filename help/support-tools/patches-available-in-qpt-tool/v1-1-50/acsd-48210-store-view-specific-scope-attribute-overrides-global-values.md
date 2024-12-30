---
title: 'ACSD-48210: Das Attribut für den spezifischen Bereich der Speicheransicht überschreibt globale Werte'
description: Wenden Sie den Patch ACSD-48210 an, um das Adobe Commerce-Problem zu beheben, dass ein *[!UICONTROL Website Scope]*-Attribut in einer bestimmten Store-Ansicht aktualisiert wird, um die Attributwerte im globalen Umfang zu überschreiben.
feature: Products, Attributes
role: Admin, Developer
exl-id: e279df44-0916-4f2e-99f2-76e123895125
source-git-commit: a84c3d296deb49d419be78f454696177a974d923
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-48210: Store-Ansicht-spezifische Bereichsattribute überschreiben globale Werte

Mit dem Patch „ACSD-48210“ wird das Problem behoben, dass beim Aktualisieren eines *[!UICONTROL Website Scope]* Attributs in einer bestimmten Store-Ansicht die Attributwerte im globalen Umfang überschrieben werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 installiert ist. Die Patch-ID ist ACSD-48210. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim Aktualisieren eines *[!UICONTROL Website Scope]* Attributs innerhalb einer bestimmten Store-Ansicht überschreiben die Attributwerte im globalen Umfang.

Der Import von Produktpreisen mit mehreren Zeilen, die denselben `SKU` und `store_view_code` gemeinsam haben, führte zu falschen Aktualisierungen der Preise im *[!UICONTROL All Store View]* und *[!UICONTROL Default Store]* Bereich. Wenn Sie das Attribut für den Website-Umfang in einer bestimmten Store-Ansicht ändern, wird der Wert des Attributs im globalen Umfang nicht mehr überschrieben.
<u>Schritte zur Reproduktion</u>:

1. Konfigurieren Sie die zu *[!UICONTROL Website]* *[!UICONTROL Catalog Price Scope]*.
1. Erstellen Sie ein einfaches Produkt mit dem Namen *SP01* und setzen Sie den Preis auf *$84.50*.
1. Importieren Sie das Produkt mit der folgenden CSV-Datei:

   ```
   sku,store_view_code,price
   SP01,default,99.99
   SP01,default,86.59
   ```

1. Überprüfen Sie den Produktpreis in den Bereichen *[!UICONTROL All Store View]* und *[!UICONTROL Default Store]* .

<u>Erwartete Ergebnisse</u>:

* Der erste nicht leere Wert wird für den *[!UICONTROL Default Store]* verwendet.
* Der *[!UICONTROL All Store View]* bleibt unverändert.

<u>Tatsächliche Ergebnisse</u>:

* Der Preis für den *[!UICONTROL All Store View]* Umfang ändert sich auf *$ 86.59*.
* Der Preis für den *[!UICONTROL Default Store]* Umfang ändert sich auf *$ 86.59*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
