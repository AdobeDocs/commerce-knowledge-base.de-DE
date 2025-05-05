---
title: 'ACSD-53722: Preisänderungen für gebündelte Produktoptionen auf 0 $'
description: Wenden Sie den ACSD-53722 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem sich der Preis der gebündelten Produktoptionen auf 0 USD ändert, wenn geplante Updates für verschiedene Bereiche aktiv werden.
feature: Products
role: Admin, Developer
exl-id: da4c25ac-78bc-4d4e-a55e-826924a099e9
source-git-commit: e587b70a270bca624fb60a1b0940c05221da3aef
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-53722: Preisänderungen für gebündelte Produktoptionen auf 0 $

Mit dem Patch ACSD-53722 wird das Problem behoben, dass der Preis der gebündelten Produktoptionen auf 0 USD geändert wird, wenn geplante Aktualisierungen für verschiedene Bereiche aktiv werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41 installiert ist. Die Patch-ID ist ACSD-53722. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Preis für gebündelte Produktoptionen ändert sich auf 0 $ , wenn geplante Aktualisierungen für verschiedene Bereiche aktiv werden.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie zwei Websites, A und B.
1. Legen Sie die Konfiguration unter **[!UICONTROL Catalog]** > **[!UICONTROL Price]** > **[!UICONTROL Catalog Price Scope]** = **[!UICONTROL Website]** fest.
1. Erstellen Sie auf den Websites A und B ein gebündeltes Produkt mit einem Festpreis:

   * Gebündelter Produktpreis = Festpreis = *0*

1. Fügen Sie ein einfaches Produkt als Dropdown-Option für das Bundle hinzu. Legen Sie die folgenden Preise fest:

   * Alle Store-Ansichten eines einfachen Produkts Preis innerhalb der gebündelten Option = *120*
   * Website eines einfachen Produkts Ein Preis innerhalb der gebündelten Option = *130*
   * Website B Preis innerhalb der gebündelten Option = *140*

1. Planen Sie eine Aktualisierung, um das gebündelte Produkt auf Website A zu deaktivieren.

<u>Erwartete Ergebnisse</u>:

Geplante Aktualisierungen für Website A wirken sich nicht auf den Preis von Website B aus.

<u>Tatsächliche Ergebnisse</u>:

Nach der geplanten Aktualisierung wird der Preis der gebündelten Produktoption auf Website B auf **$ 0 %**.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
