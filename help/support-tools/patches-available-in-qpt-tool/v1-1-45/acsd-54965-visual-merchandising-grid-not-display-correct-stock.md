---
title: 'ACSD-54965: [!UICONTROL Visual Merchandising] Raster zeigt nicht das richtige Lager an'
description: Wenden Sie den Patch ACSD-54965 an, um das Adobe Commerce-Problem zu beheben, bei dem das Raster "[!UICONTROL Visual Merchandising]"nicht das richtige Lager anzeigt, wenn ein Produkt einem benutzerdefinierten Lager zugewiesen ist.
feature: Merchandising, Categories
role: Admin, Developer
exl-id: 13d98f55-ca2c-4064-b66f-ab2cdeb37382
source-git-commit: 4f05117aa42dec1f56e4986ffd22d1a68bf5cea2
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-54965: [!UICONTROL Visual Merchandising] Raster zeigt nicht das richtige Lager an

Der Patch ACSD-54965 behebt das Problem, dass das Raster [!UICONTROL Visual Merchandising] nicht das richtige Lager anzeigt, wenn ein Produkt einem benutzerdefinierten Lager zugewiesen wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 installiert ist. Die Patch-ID ist ACSD-54965. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Raster [!UICONTROL Visual Merchandising] zeigt nicht das richtige Lager an, wenn ein Produkt einem benutzerdefinierten Lager zugewiesen wird.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine neue Quelle.
1. Erstellen Sie ein neues Lager.
1. Erstellen Sie zwei Produkte:
   * Ein Produkt mit benutzerdefiniertem Lager.
   * Ein Produkt, das nur den Standardbestand aufweist.
1. Fügen Sie diese Produkte einer Kategorie hinzu.
1. Wechseln Sie zum Raster [!UICONTROL visual Merchandising] (*[!UICONTROL Products in Category]*).

<u>Tatsächliche Ergebnisse</u>:

In den *[!UICONTROL All Store Views]* -Bereichen zeigt das Produkt mit benutzerdefiniertem Lager keine Menge an. Erst wenn der Bereich *[!UICONTROL Default Store View]* ausgewählt ist, zeigt das benutzerdefinierte Lager die Menge des Produkts an.

<u>Erwartete Ergebnisse</u>:

Das Raster zeigt alle Lagerinformationen an, wenn der Umfang *[!UICONTROL All Store Views]* beträgt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
