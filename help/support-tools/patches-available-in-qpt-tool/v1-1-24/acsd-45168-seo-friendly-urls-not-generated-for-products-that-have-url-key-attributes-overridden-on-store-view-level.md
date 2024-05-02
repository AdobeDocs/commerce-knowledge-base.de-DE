---
title: 'ACSD-45168: SEO-freundliche URLs, die nicht für Produkte generiert wurden, deren Attribute url_key überschrieben wurden'
description: Wenden Sie den Patch ACSD-45168 an, um das Adobe Commerce-Problem zu beheben, bei dem SEO-freundliche URLs nicht für Produkte generiert wurden, deren Attribute url_key auf Store-Ansichtsebene überschrieben wurden.
exl-id: cdba42ac-3c96-439b-befa-f0a13587b5d9
feature: Attributes, Cache, Categories, Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-45168: SEO-freundliche URLs, die nicht für Produkte generiert wurden, deren Attribute url_key überschrieben wurden

Der Patch ACSD-45168 behebt das Problem, dass SEO-freundliche URLs nicht für Produkte generiert werden, deren Attribute url_key auf der Store-Ansichtsebene überschrieben werden. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 ist installiert. Die Patch-ID ist ACSD-45168. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

SEO-freundliche URLs werden nicht für Produkte generiert, bei denen url_key -Attribute auf der Store-Ansichtsebene überschrieben werden.

<u>Zu reproduzierende Schritte</u>:

1. Stellen Sie die Konfiguration wie folgt ein, indem Sie zum **[!UICONTROL Commerce Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]**:
   * [!UICONTROL Use Categories Path for Product URLs] = *Ja*
   * [!UICONTROL Generate "category/product" URL Rewrites] = *Ja*
1. Bereinigen Sie den Konfigurations-Cache.
1. Erstellen Sie zwei Kategorien: [!UICONTROL Category 1] und [!UICONTROL Category 2].
1. Erstellen Sie zwei Produkte: [!UICONTROL Product 1] in [!UICONTROL Category 1], [!UICONTROL Product 2] in [!UICONTROL Category 1].
1. Ändern Sie den Umfang in [!UICONTROL Default Store View] für [!UICONTROL Product 1].
1. Deaktivieren Sie die optionale URL [!UICONTROL Key] in [!UICONTROL Search Engine Optimization].
1. Speichern Sie das Produkt.
1. Zurück zu [!UICONTROL All Store Views].
1. Hinzufügen [!UICONTROL Product 1] nach [!UICONTROL Category 2]und fügen Sie [!UICONTROL Product 2] nach [!UICONTROL Category 2].
1. Überprüfen Sie die [!UICONTROL url_rewrite] Tabelle oder [!UICONTROL Marketing] > [!UICONTROL SEO & Search] > [!UICONTROL URL Rewrites].

<u>Erwartete Ergebnisse</u>:

Die SEO-freundliche URL für [!UICONTROL Category 2] erstellt für [!UICONTROL Product 1].

<u>Tatsächliche Ergebnisse</u>:

Die SEO-freundliche URL für [!UICONTROL Category 2] fehlt für [!UICONTROL Product 1] weil das URL-Schlüsselattribut für den Umfang der Store-Ansicht überschrieben wurde.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
