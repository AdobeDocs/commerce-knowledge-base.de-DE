---
title: 'ACSD-60303: Problem mit der Platzierung von Admin-Aufträgen mit aktivierter HTML-Minimierung behoben'
description: Wenden Sie den ACSD-60303 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem eine Bestellung vom Administrator nicht aufgegeben werden kann, wenn die HTML-Minimierung aktiviert ist.
feature: Orders
role: Admin, Developer
exl-id: 06f7fc4f-8cdc-47c6-a706-52b8e70d66e0
source-git-commit: a84c3d296deb49d419be78f454696177a974d923
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-60303: Problem mit der Platzierung von Admin-Aufträgen mit aktivierter HTML-Minimierung behoben

Der Patch ACSD-60303 behebt das Problem, dass eine Bestellung vom Administrator nicht aufgegeben werden kann, wenn die HTML-Minimierung aktiviert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 installiert ist. Die Patch-ID ist ACSD-60303. Beachten Sie, dass das Problem voraussichtlich in 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p8

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p9 - 2.4.4-p10, 2.4.5-p8 - 2.4.5-p9, 2.4.6-p6 - 2.4.6-p7

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Bestellungen können nicht über das Admin-Bedienfeld aufgegeben werden, wenn die HTML-Minimierung aktiviert ist.

<u>Schritte zur Reproduktion</u>:

1. HTML-Minimierung aktivieren.
1. Legen Sie die **[!UICONTROL Application Mode]** auf *[!UICONTROL Production]* fest.
1. Erstellen Sie eine Bestellung im Admin-Bedienfeld.

<u>Erwartete Ergebnisse</u>:

Die Bestellung wurde erfolgreich aufgegeben.

<u>Tatsächliche Ergebnisse</u>:

Die Bestellung wird nicht erstellt und der folgende Fehler wird protokolliert:

`report.CRITICAL: ParseError: syntax error, unexpected token "<<" in var/view_preprocessed/pub/static/vendor/magento/module-gift-wrapping/view/adminhtml/templates/order/create/info.phtml:1`

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
