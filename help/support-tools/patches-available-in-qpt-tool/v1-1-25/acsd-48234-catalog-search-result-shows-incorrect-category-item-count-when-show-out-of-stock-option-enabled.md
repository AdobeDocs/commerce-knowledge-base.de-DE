---
title: '"ACSD-48234: Katalogsuchergebnis falsche Kategorieelementanzahl, wenn [!UICONTROL Display Out of Stock Products] enabled'''
description: Wenden Sie den Patch ACSD-48234 an, um das Adobe Commerce-Problem zu beheben, bei dem das Katalogsuchergebnis eine falsche Kategorieelementanzahl anzeigt, wenn die Variable [!UICONTROL Display Out of Stock Products] aktiviert ist.
exl-id: 8e70fe73-d550-4e11-b25e-84955e136d12
feature: Admin Workspace, Categories, Catalog Management, Orders, Products, Search
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-48234: Katalogsuchergebnis zeigt falsche Kategorieelementanzahl an **[!UICONTROL Display Out of Stock Products]** enabled

Der Patch ACSD-48234 behebt das Problem, dass das Katalogsuchergebnis eine falsche Kategorieelementanzahl anzeigt, wenn die Variable **[!UICONTROL Display Out of Stock Products]** aktiviert ist. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 ist installiert. Die Patch-ID lautet ACSD-48234. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.


## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.5 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Katalogsuchergebnis zeigt eine falsche Kategorieelementanzahl an, wenn die Variable **[!UICONTROL Display Out of Stock Products]** aktiviert ist.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** und öffnen **[!UICONTROL color]** -Attribut.
1. Fügen Sie zwei Optionen hinzu, z. B. orange und grün. Speichern Sie das Attribut.
1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]** und fügen Sie **[!UICONTROL color]** -Attribut **[!UICONTROL Default]** -Attributsatz.
1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** und **[!UICONTROL Display Out of Stock Products]** nach _Ja_.
1. Kategorie &quot;cat1&quot;erstellen.
1. Erstellen Sie zwei Produkte:
   1. Name: prod1, Farbe: orange, Kategorien: cat1.
   1. Name: prod2, Farbe: grün, Kategorien: cat1.
1. Öffnen Sie die Kategorie &quot;cat1&quot;auf der Storefront.
1. Wählen Sie die orangefarbene Farbe in der Navigationsschicht aus.

<u>Erwartete Ergebnisse</u>:

Es wird nur das Produkt prod1 angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Es werden sowohl die Produkte prod1 als auch prod2 angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
