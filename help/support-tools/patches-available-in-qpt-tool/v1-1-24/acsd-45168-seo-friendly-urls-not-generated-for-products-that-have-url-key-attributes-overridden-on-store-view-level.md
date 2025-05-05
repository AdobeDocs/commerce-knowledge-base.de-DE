---
title: 'ACSD-45168: SEO-freundliche URLs werden nicht für Produkte generiert, bei denen url_key-Attribute überschrieben wurden'
description: Wenden Sie den Patch „ACSD-45168“ an, um das Adobe Commerce-Problem zu beheben, dass SEO-freundliche URLs für Produkte, bei denen url_key-Attribute auf Store-Ansichtsebene überschrieben wurden, nicht generiert werden.
exl-id: cdba42ac-3c96-439b-befa-f0a13587b5d9
feature: Attributes, Cache, Categories, Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-45168: SEO-freundliche URLs werden nicht für Produkte generiert, bei denen url_key-Attribute überschrieben wurden

Der Patch ACSD-45168 behebt das Problem, dass SEO-freundliche URLs nicht für Produkte generiert werden, bei denen url_key-Attribute auf Store-Ansichtsebene überschrieben wurden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 installiert ist. Die Patch-ID ist ACSD-45168. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

SEO-freundliche URLs werden nicht für Produkte generiert, bei denen url_key-Attribute auf Store-Ansichtsebene überschrieben wurden.

<u>Schritte zur Reproduktion</u>:

1. Legen Sie die Konfiguration wie folgt fest, indem Sie zu **[!UICONTROL Commerce Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]** gehen:
   * [!UICONTROL Use Categories Path for Product URLs] = *Ja*
   * [!UICONTROL Generate "category/product" URL Rewrites] = *Ja*
1. Bereinigen Sie den Konfigurations-Cache.
1. Erstellen Sie zwei Kategorien: [!UICONTROL Category 1] und [!UICONTROL Category 2].
1. Erstellen Sie zwei Produkte: [!UICONTROL Product 1] in [!UICONTROL Category 1], [!UICONTROL Product 2] in [!UICONTROL Category 1].
1. Ändern Sie den Bereich für [!UICONTROL Product 1] in [!UICONTROL Default Store View] .
1. Deaktivieren Sie die optionale URL-[!UICONTROL Key] in [!UICONTROL Search Engine Optimization].
1. Speichern Sie das Produkt.
1. Wechseln Sie zurück zu [!UICONTROL All Store Views].
1. Fügen Sie [!UICONTROL Product 1] zu [!UICONTROL Category 2] hinzu und fügen Sie [!UICONTROL Product 2] zu [!UICONTROL Category 2] hinzu.
1. Überprüfen Sie die [!UICONTROL url_rewrite] Tabelle oder [!UICONTROL Marketing] > [!UICONTROL SEO & Search] > [!UICONTROL URL Rewrites].

<u>Erwartete Ergebnisse</u>:

Die SEO-freundliche URL für [!UICONTROL Category 2] wird für [!UICONTROL Product 1] erstellt.

<u>Tatsächliche Ergebnisse</u>:

Die SEO-freundliche URL für [!UICONTROL Category 2] fehlt für [!UICONTROL Product 1], da das URL-Schlüsselattribut für den Bereich der Store-Ansicht überschrieben wurde.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
