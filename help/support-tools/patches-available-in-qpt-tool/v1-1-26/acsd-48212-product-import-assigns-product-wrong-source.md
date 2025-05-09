---
title: 'ACSD-48212: Produktimport weist Produkt einer falschen Quelle zu'
description: Wenden Sie den Patch ACSD-48212 an, um das Adobe Commerce-Problem zu beheben, bei dem der Produktimport das Produkt der falschen Quelle zuweist.
exl-id: b3426f62-f73a-4b76-8e0e-544a9133720f
feature: Admin Workspace, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-48212: Produktimport weist Produkt einer falschen Quelle zu

Mit dem Patch ACSD-48212 wird das Problem behoben, dass beim Produktimport das Produkt der falschen Quelle zugewiesen wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 installiert ist. Die Patch-ID ist ACSD-48212. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Produktimport weist das Produkt der falschen Quelle zu.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine sekundäre Bestandsquelle.
1. Erstellen Sie ein Produkt nur mit der standardmäßigen Bestandsquelle.
1. Exportieren Sie das Produkt.
1. `bin/magento cron:run` ausführen.
1. Öffnen Sie **[!UICONTROL Catalog]** > **[!UICONTROL Prdoucts]**.
1. Wählen Sie das Produkt im Raster aus.
1. Heben Sie die Zuweisung des Lagers über das Menü *[!UICONTROL mass action]* auf.
1. `bin/magento cron:run` ausführen.
1. Weisen Sie die sekundäre Quelle über das Menü *[!UICONTROL mass action]* zu.
1. `bin/magento cron:run` ausführen.
1. Löschen Sie das Produkt über das Menü *[!UICONTROL mass action]* .
1. `bin/magento cron:run` ausführen.
1. Importieren Sie das Produkt mit der zuvor exportierten CSV-Datei.
1. Quellzuweisung überprüfen.

<u>Erwartete Ergebnisse</u>:

Das Produkt ist nur der Standardquelle zugewiesen.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt ist sowohl der standardmäßigen als auch der sekundären Quelle zugewiesen.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
