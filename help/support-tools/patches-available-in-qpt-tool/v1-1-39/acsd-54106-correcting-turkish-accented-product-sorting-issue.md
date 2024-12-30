---
title: 'ACSD-54106: Korrigieren der Schriftzeichensortierung mit türkischem Akzent in der Produktkategorie'
description: Wenden Sie den Patch ACSD-54106 an, um das Adobe Commerce-Problem zu beheben, bei dem die Sortierung von Kategorieprodukten nach Name für Zeichen mit türkischem Akzent falsch ist.
feature: Categories, Products, Search
role: Admin
exl-id: 80386ded-4ada-4822-b073-f477ca123093
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-54106: Korrigieren der Schriftzeichensortierung mit türkischem Akzent in der Produktkategorie

Der Patch ACSD-54106 behebt das Problem, dass die Sortierung nach Produktname für Zeichen mit türkischem Akzent falsch ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.39 installiert ist. Die Patch-ID ist ACSD-54106. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.4-p5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Sortierung von Produkten innerhalb von Kategorien nach Namen ist bei Zeichen mit türkischem Akzent falsch.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich beim Admin Panel an.
1. Erstellen Sie einfache Produkte mit den folgenden Namen und weisen Sie sie einer beliebigen Kategorie zu:

* Benennen Sie
* Name ç
* Name D
* Name
* Name M
* Name Ö
* Name ü
* Name Y
* Z benennen

1. Navigieren Sie zur Storefront und rufen Sie die Kategorie auf, die die Produkte enthält.
1. Ändern Sie die Sortierreihenfolge in *[!UICONTROL By Name]*.

<u>Erwartete Ergebnisse</u>:

Die Produkte werden in der folgenden Reihenfolge korrekt sortiert:

* Benennen Sie
* Name ç
* Name D
* Name
* Name M
* Name Ö
* Name ü
* Name Y
* Z benennen

<u>Tatsächliche Ergebnisse</u>:

Produkte werden fälschlicherweise in der folgenden Reihenfolge sortiert:

* Benennen Sie
* Name D
* Name M
* Name Y
* Z benennen
* Name ç
* Name Ö
* Name ü
* Name

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
