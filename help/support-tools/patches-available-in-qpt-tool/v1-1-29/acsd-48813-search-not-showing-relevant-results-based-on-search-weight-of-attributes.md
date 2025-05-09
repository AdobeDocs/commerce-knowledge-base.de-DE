---
title: 'ACSD-48813: Die Suche zeigt keine relevanten Ergebnisse basierend auf der Suchgewichtung der Attribute an'
description: Wenden Sie den Patch ACSD-48813 an, um das Adobe Commerce-Problem zu beheben, bei dem die Suche keine relevanten Ergebnisse basierend auf der Suchgewichtung der Attribute anzeigt.
exl-id: 089e3ab3-0dfa-4f81-85c7-f6060f326d97
feature: Admin Workspace, Attributes, Search
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-48813: Die Suche zeigt keine relevanten Ergebnisse basierend auf der Suchgewichtung der Attribute an

Mit dem Patch ACSD-48813 wird das Problem behoben, dass die Suche keine relevanten Ergebnisse basierend auf der Suchgewichtung der Attribute anzeigt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 installiert ist. Die Patch-ID ist ACSD-48813. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Suche zeigt keine relevanten Ergebnisse basierend auf der Suchgewichtung der Attribute an.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie Adobe Commerce mit Beispieldaten.
1. Legen Sie die Suchmaschine als [!DNL Elasticsearch] fest.
1. Melden Sie sich als Administrator an.
1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Products]**.
1. Öffnen Sie das *name*-Attribut.
1. Öffnen Sie die Registerkarte Storefront-*[!UICONTROL Properties]* .
1. Wählen Sie [!UICONTROL Search Weight] = *10* aus dem Dropdown-Wert aus.
1. Klicken Sie auf **[!UICONTROL Save Attribute]**.
1. Öffnen Sie nun die Storefront und suchen Sie nach dem Wort *Zurück*.

<u>Erwartete Ergebnisse</u>:

Rucksackprodukte werden oben in den Suchergebnissen zurückgegeben.

<u>Tatsächliche Ergebnisse</u>:

Rucksackprodukte werden mitten in den Suchergebnissen zurückgegeben.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
