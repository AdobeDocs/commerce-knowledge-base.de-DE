---
title: 'ACSD-56616: Schaufenster-Anzeige von gebündelten Produkten während einfacher Lagerknappheit'
description: Wenden Sie den Patch ACSD-56616 an, um das Adobe Commerce-Problem zu beheben, bei dem gebündelte Produkte unerwartet in der Storefront angezeigt werden, wenn alle zugehörigen einfachen Produkte nicht vorrätig sind.
feature: Products
role: Admin, Developer
exl-id: 6cf8e15d-38a5-42b6-aee7-67410b501404
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-56616: Schaufenster-Anzeige von gebündelten Produkten während einfacher Lagerknappheit.

Mit dem Patch ACSD-56616 wird das Problem behoben, dass gebündelte Produkte unerwartet in der Storefront angezeigt werden, wenn alle zugehörigen einfachen Produkte nicht vorrätig sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 installiert ist. Die Patch-ID ist ACSD-56616. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Falsche Schaufensteranzeige von gebündelten Produkten während einfacher Lagerknappheit.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine neue Website/Storefront/Store-Front.
1. Erstellen Sie eine neue Quelle.
1. Erstellen Sie ein neues Lager und weisen Sie es der neu erstellten Website zu.
1. Indexer so konfigurieren, dass die Aktualisierung planmäßig erfolgt.
1. Generieren Sie zwei einfache Produkte, S1 (Menge = 1) und S2 (Menge = 1), und weisen Sie sie dem neuen Lager und der neuen Website zu.
1. Erstellen Sie *gebündeltes1*-Produkt, verknüpfen Sie es mit einer neuen Website und platzieren Sie es in der Kategorie *CAT*.
1. Definieren Sie zwei erforderliche Dropdown-Optionen und verknüpfen Sie einfache *S1* mit Option1 und *S2* mit Option2.
1. Speichern Sie die Produkte.
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** und aktivieren Sie *Store-Code zur URL hinzufügen* = *Ja*.
1. Öffnen Sie die Storefront und kaufen Sie das gebündelte Produkt.
1. Führen Sie Cron zweimal aus.
1. Kehren Sie zur Kategorie *CAT* zurück.

<u>Erwartete Ergebnisse</u>:

Das *Bundle1*-Produkt ist nicht vorrätig.

<u>Tatsächliche Ergebnisse</u>:

Das *Bundle1* Produkt ist sichtbar mit Preis = *$0*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
