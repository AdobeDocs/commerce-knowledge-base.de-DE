---
title: 'ACSD-56023: Widget-Inhalte werden auf der CMS-Seite nicht aktualisiert'
description: Wenden Sie den Patch „ACSD-56023“ an, um das Adobe Commerce-Problem zu beheben, bei dem der Inhalt des Widgets auf der CMS-Seite nicht aktualisiert wird
feature: CMS
role: Admin, Developer
exl-id: 2ff33b1c-ae92-4c59-83d2-e252bf543bab
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-56023: Widget-Inhalte werden auf der CMS-Seite nicht aktualisiert

Der Patch ACSD-56023 behebt das Problem, dass der Widget-Inhalt auf der CMS-Seite nicht aktualisiert wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 installiert ist. Die Patch-ID ist ACSD-56023. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Widget-Inhalte werden auf der CMS-Seite nicht aktualisiert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie einige Produkte.
1. Erstellen Sie die neue CMS-Seite und fügen Sie dem Inhalt das Widget „Neue Produkte“ hinzu:

   ```
      {{widget type="Magento\Catalog\Block\Product\Widget\NewWidget" display_type="new_products" show_pager="1" products_per_page="5" products_count="10" template="product/widget/new/content/new_grid.phtml" page_var_name="pnetpm"}} 
   ```

1. Öffnen Sie die erstellte Seite in der Storefront. Stellen Sie sicher, dass Sie es zwischenspeichern.
1. Öffnen Sie in Admin **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Wählen Sie ein beliebiges Produkt zur Bearbeitung aus und wechseln Sie **[!UICONTROL Set Product as New]** zu *Ja*.
1. Navigieren Sie erneut zur erstellten Seite mit der ** CMS in der Storefront.

<u>Erwartete Ergebnisse</u>:

Die Seite enthält *Widget „Neue Produkte* mit den Produkten.

<u>Tatsächliche Ergebnisse</u>:

Die Seite enthält nicht das *Widget „Neue Produkte* und die neuen Produkte werden nicht angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
