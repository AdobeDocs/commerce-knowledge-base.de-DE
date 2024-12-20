---
title: 'ACSD-48210: Store view specific scope attribute overrides global values'
description: Wenden Sie den Patch ACSD-48210 an, um das Adobe Commerce-Problem zu beheben, das beim Aktualisieren eines *[!UICONTROL Website Scope]* -Attributs in einer bestimmten Store-Ansicht auftritt, wodurch die Attributwerte im globalen Gültigkeitsbereich außer Kraft gesetzt werden.
feature: Products, Attributes
role: Admin, Developer
exl-id: e279df44-0916-4f2e-99f2-76e123895125
source-git-commit: a84c3d296deb49d419be78f454696177a974d923
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-48210: Store view specific scope attributes override global values

Der Patch ACSD-48210 behebt das Problem, dass beim Aktualisieren eines *[!UICONTROL Website Scope]* -Attributs in einer bestimmten Store-Ansicht die Attributwerte im globalen Gültigkeitsbereich außer Kraft gesetzt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 installiert ist. Die Patch-ID lautet ACSD-48210. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Beim Aktualisieren eines *[!UICONTROL Website Scope]* -Attributs in einer bestimmten Store-Ansicht werden die Attributwerte im globalen Gültigkeitsbereich überschrieben.

Der Import von Produktpreisen mit mehreren Zeilen, die dieselben `SKU` und `store_view_code` aufweisen, führte zu falschen Aktualisierungen der Preise in den Bereichen *[!UICONTROL All Store View]* und *[!UICONTROL Default Store]*. Durch das Ändern des Attributs zum Website-Umfang in einer bestimmten Store-Ansicht wird der Wert des Attributs im globalen Gültigkeitsbereich nicht mehr überschrieben.
<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren Sie die *[!UICONTROL Catalog Price Scope]* auf *[!UICONTROL Website]*.
1. Erstellen Sie ein einfaches Produkt mit dem Namen *SP01* und legen Sie den Preis auf *$84.50* fest.
1. Importieren Sie das Produkt mit der folgenden CSV-Datei, die unten bereitgestellt wird:

   ```
   sku,store_view_code,price
   SP01,default,99.99
   SP01,default,86.59
   ```

1. Überprüfen Sie den Produktpreis in den Gültigkeitsbereichen *[!UICONTROL All Store View]* und *[!UICONTROL Default Store]*.

<u>Erwartete Ergebnisse</u>:

* Der erste nicht leere Wert wird für den Bereich *[!UICONTROL Default Store]* verwendet.
* Der Gültigkeitsbereich *[!UICONTROL All Store View]* bleibt unverändert.

<u>Tatsächliche Ergebnisse</u>:

* Der Gültigkeitspreis von *[!UICONTROL All Store View]* ändert sich in *$86.59*.
* Der Gültigkeitspreis von *[!UICONTROL Default Store]* ändert sich in *$86.59*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
