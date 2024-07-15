---
title: "ACSD-53628: CSV-Verkaufsauftragsbericht zeigt falsche Sonderzeichen an"
description: Wenden Sie den Patch ACSD-53628 an, um das Adobe Commerce-Problem zu beheben, bei dem der CSV-Verkaufsauftragsbericht falsche Sonderzeichen anzeigt.
feature: Orders, Data Import/Export
role: Admin, Developer
exl-id: d898fdb8-cab9-49ab-ad8e-43feadf49aa0
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-53628: CSV-Verkaufsauftragsbericht zeigt falsche Sonderzeichen an

Der Patch ACSD-53628 behebt das Problem, dass der CSV-Verkaufsauftragsbericht falsche Sonderzeichen anzeigt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.37 installiert ist. Die Patch-ID ist ACSD-53628. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden): 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden): 2.3.7 - 2.4.6 - p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der CSV-Bestellbericht zeigt falsche Sonderzeichen an.

<u>Zu reproduzierende Schritte</u>:

1. Ändern Sie **[!UICONTROL Base Currency]** und **[!UICONTROL Default Display Currency]** in der Währungseinstellung in Euro.
1. Bestellung aufgeben.
1. Wechseln Sie in der Admin-Seitenleiste zu **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Wählen Sie Datumswerte aus. Klicken Sie auf **[!UICONTROL Show Report]**. Klicken Sie auf **[!UICONTROL Export]** , um die CSV zu exportieren.

<u>Erwartete Ergebnisse</u>:

Sonderzeichen in einer exportierten CSV-Datei werden in Excel korrekt angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Der CSV-Bestellbericht zeigt Sonderzeichen falsch an.


## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
