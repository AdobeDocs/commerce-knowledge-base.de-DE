---
title: 'ACSD-51700: Fehler beim Wechseln der Store-Ansichten auf der herunterladbaren Produktebearbeitungsseite'
description: Wenden Sie den Patch ACSD-51700 an, um das Adobe Commerce-Problem zu beheben, bei dem beim Wechseln der Store-Ansichten auf einer herunterladbaren Produktebearbeitungsseite im Admin ein Fehler auftritt.
feature: Products
role: Admin
exl-id: 652876a5-275d-437f-9cb3-baf4e7b23aae
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51700: Fehler beim Wechseln der Store-Ansichten auf der herunterladbaren Produktebearbeitungsseite

Der Patch ACSD-51700 behebt das Problem, dass beim Wechsel der Store-Ansichten auf einer herunterladbaren Produktebearbeitungsseite im Admin ein Fehler auftritt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.33 installiert ist. Die Patch-ID ist ACSD-51700. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6 - p1

## Problem

Beim Wechseln der Store-Ansichten auf einer herunterladbaren Produktbearbeitungsseite in der Admin-Konsole tritt ein Fehler auf.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein herunterladbares Produkt mit einem Namen, [!DNL SKU] und einem Preis. Fügen Sie keine Links hinzu und speichern Sie das Produkt.
1. Wechseln Sie von allen Store-Ansichten zur standardmäßigen Store-Ansicht.
1. Erstellen Sie einen Link für das herunterladbare Produkt und speichern Sie es.
1. Wechseln Sie von der standardmäßigen Store-Ansicht zu allen Store-Ansichten.

<u>Erwartete Ergebnisse</u>:

Die verknüpften Produkte sind sichtbar.

<u>Tatsächliche Ergebnisse</u>:

Der folgende Fehler wird angezeigt:

*Veraltete Funktion: number_format(): Die Übergabe von null an den Parameter #1 ($num) des Typs &quot;float&quot;wird in vendor/magento/module-downloadable/Ui/DataProvider/Product/Form/Modifier/Data/Links.php in Zeile 228* nicht mehr unterstützt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
