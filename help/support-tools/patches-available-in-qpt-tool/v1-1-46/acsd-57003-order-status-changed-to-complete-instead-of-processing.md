---
title: 'ACSD-57003: Der Bestellstatus ändert sich in „Abgeschlossen“, anstatt in „Verarbeitung läuft“ zu wechseln'
description: Wenden Sie den Patch ACSD-57003 an, um das Adobe Commerce-Problem zu beheben, bei dem sich der Bestellstatus in „Abgeschlossen“ ändert, anstatt in „Verarbeitung läuft“ zu wechseln.
feature: Orders, Invoices, Shipping/Delivery
role: Admin, Developer
exl-id: c3c59185-c447-46fa-b404-6c4a4a300315
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-57003: Der Bestellstatus ändert sich in *Abgeschlossen* anstatt in *Verarbeitung* zu wechseln

Mit dem Patch „ACSD-57003“ wird das Problem behoben, dass der Bestellstatus in &quot;*&quot;*, anstatt in &quot;*&quot;*. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.46 installiert ist. Die Patch-ID ist ACSD-57003. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Bestellstatus ändert sich in *Abgeschlossen* anstatt in *Verarbeitung* zu wechseln, wenn eine Bestellung teilweise zurückerstattet und teilweise versendet wird.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine Bestellung mit zwei konfigurierbaren Produkten.
1. Alle Positionen fakturieren.
1. Versand nur den ersten Artikel.
1. Gutschrift nur für den versendeten Artikel zurückerstatten/erstellen (*erster Artikel*).
1. Überprüfen Sie den Bestellstatus.

<u>Erwartete Ergebnisse</u>:

Der Bestellstatus muss den Status _Verarbeitung_ aufweisen.

<u>Tatsächliche Ergebnisse</u>:

Der Auftragsstatus ändert sich *Abgeschlossen* nachdem eine Gutschrift für den teilweise gelieferten Artikel erstellt wurde.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
