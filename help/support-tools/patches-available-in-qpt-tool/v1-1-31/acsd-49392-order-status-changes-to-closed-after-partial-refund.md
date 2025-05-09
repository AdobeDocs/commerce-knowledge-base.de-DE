---
title: 'ACSD-49392: Auftragsstatus ändert sich nach teilweiser Rückerstattung in Geschlossen'
description: Wenden Sie den Patch ACSD-49392 an, um das Adobe Commerce-Problem zu beheben, bei dem sich der Bestellstatus nach einer teilweisen Rückerstattung für ein gebündeltes Produkt in „Geschlossen“ ändert.
exl-id: fca6f502-e224-4444-b0d0-f823853c9458
feature: Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-49392: Auftragsstatus ändert sich nach teilweiser Rückerstattung in Geschlossen

Mit dem Patch ACSD-49392 wird das Problem behoben, dass sich der Bestellstatus nach einer teilweisen Rückerstattung für ein gebündeltes Produkt in „Geschlossen“ ändert. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.31 installiert ist. Die Patch-ID ist ACSD-49392. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.3.7-p4 und 2.4.1 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Bestellstatus ändert sich nach einer teilweisen Rückerstattung für ein gebündeltes Produkt in „Geschlossen“.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich bei Adobe Commerce an und erstellen Sie ein beliebiges gebündeltes Produkt oder verwenden Sie das vorhandene gebündelte Produkt.
1. Bestellen Sie mit diesem gebündelten Produkt eine Menge von mehr als 1.
1. Gehen Sie zu Admin, öffnen Sie die in Schritt 2 erstellte Bestellung über **[!UICONTROL Sales]** > **[!UICONTROL Order]** und erstellen Sie eine Rechnung. Beobachten Sie den Bestellstatus. Er wird verarbeitet.
1. Erstellen Sie eine teilweise Gutschrift (erstatten Sie nicht für alle Produkte im Bundle).
1. Überprüfen Sie den Bestellstatus.

<u>Erwartete Ergebnisse</u>

Nachdem eine teilweise Gutschrift für das gebündelte Produkt erstellt wurde, ist der Bestellstatus in Bearbeitung.

<u>Tatsächliche Ergebnisse</u>

Nachdem Sie eine teilweise Gutschrift für das gebündelte Produkt erstellt haben, ist der Bestellstatus abgeschlossen.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
