---
title: 'ACSD-51497: Katalogseite kann nicht nach benutzerdefiniertem Attribut des Typs Dropdown sortiert werden.'
description: Wenden Sie den Patch ACSD-51497 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Kunde eine Katalogseite nicht nach einem benutzerdefinierten Attribut des Typs Dropdown sortieren kann.
feature: Attributes, Cache, Catalog Management, Categories
role: Developer
exl-id: 60a4f375-9b9a-4026-9dc7-d9f847a75656
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# ACSD-51497: Katalogseite kann nicht nach benutzerdefiniertem Attribut des Typs sortiert werden *Dropdown*

Der Patch ACSD-51497 behebt das Problem, dass ein Kunde eine Katalogseite nicht nach einem benutzerdefinierten Attribut des Typs sortieren kann *Dropdown*. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 installiert ist. Die Patch-ID ist ACSD-51497. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Ein Kunde kann eine Katalogseite nicht nach einem benutzerdefinierten Attribut des Typs *Dropdown*.

<u>Zu reproduzierende Schritte</u>

1. Erstellen Sie etwa sechs einfache Produkte und weisen Sie sie einer Kategorie zu.
1. Erstellen Sie ein Produktattribut, um es als Sortieroption auf den Listenseiten hinzuzufügen.

   * Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Add New Attribute]**.
   * Im **[!UICONTROL Properties]** -Registerkarte Folgendes festlegen:

      * *[!UICONTROL Default Label]* = *test*
      * *[!UICONTROL Catalog Input Type]* für Store Owner = *Dropdown*
      * *[!UICONTROL Options]*:

         * *first*
         * *second*
         * *third*
         * *vierte*

   * Im **[!UICONTROL Storefront Properties]** -Registerkarte Folgendes festlegen:

      * *[!UICONTROL Used for sorting in product listing]* = *Ja*
      * Belassen Sie alle anderen Optionen als *Standard*.

1. Zuweisen der *test* -Attribut *Standard* -Attribut in **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. Konfigurieren der zu verwendenden Produkte *test* -Attributwerten.

   * SKU: s00001, Test: vierte
   * SKU: s00002, Test: dritte
   * SKU: s00003, Test: Sekunde
   * SKU: s00004, test: first
   * SKU: s00005, Test: vierte
   * SKU: s00006, Test: dritte

1. Neuindizieren und leeren Sie den Cache.
1. Gehen Sie zur Kategorie in der Storefront.
1. Sortieren nach *test* -Attribut.

<u>Erwartete Ergebnisse</u>:

Die Produkte werden nach *test* -Attribut.

<u>Tatsächliche Ergebnisse</u>:

Die Produkte werden nicht nach der *test* -Attribut.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
