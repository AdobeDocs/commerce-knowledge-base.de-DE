---
title: "ACSD-50621: Die Stufenpreise für verschiedene Websites im freigegebenen Katalog sind nicht sichtbar."
description: Wenden Sie den Patch ACSD-50621 an, um das Adobe Commerce-Problem zu beheben, bei dem die Stufenpreise für verschiedene Websites im freigegebenen Katalog nicht sichtbar sind, wenn sie in einer Umgebung mit mehreren Websites bearbeitet werden.
exl-id: 6d6635bc-4f76-4e2f-9bc7-0276cced8ca9
feature: Catalog Management, Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-50621: Stufentarife für verschiedene Websites im freigegebenen Katalog sind nicht sichtbar

Der Patch ACSD-50621 behebt das Problem, dass die Stufenpreise für verschiedene Websites im freigegebenen Katalog nicht sichtbar sind, wenn sie in einer Umgebung mit mehreren Websites bearbeitet werden. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.32 installiert ist. Die Patch-ID ist ACSD-50621. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Statuspreise für verschiedene Websites im freigegebenen Katalog sind nicht sichtbar, wenn sie in einer Umgebung mit mehreren Websites bearbeitet werden.

<u>Zu reproduzierende Schritte</u>:

1. Legen Sie die **[!UICONTROL Catalog Price Scope]** nach **[!UICONTROL Website]**.
1. Erstellen Sie eine zusätzliche Website, einen Store und eine Storeübersicht.
1. Erstellen Sie ein einfaches Produkt und weisen Sie es allen Websites zu.
1. Erstellen Sie einen benutzerdefinierten freigegebenen Katalog.
1. Navigieren Sie zu **[!UICONTROL Set Pricing and Structure]** für den von Ihnen erstellten benutzerdefinierten freigegebenen Katalog.
1. In Schritt 1: Produkte für den Katalog auswählen. Fügen Sie das von Ihnen erstellte einfache Produkt hinzu.
1. In Schritt 2: Festlegen benutzerdefinierter Preise und Klicken **[!UICONTROL Configure]**.
1. Legen Sie für verschiedene Websites unterschiedliche Preise fest.
1. Auswählen **[!UICONTROL Done]** und auf **[!UICONTROL Generate Catalog]** und klicken Sie anschließend auf **[!UICONTROL Save]**.
1. Führen Sie cron aus.
1. Navigieren Sie zu **[!UICONTROL Set Pricing and Structure]** > **[!UICONTROL Configure]** > **[!UICONTROL Next]** > **[!UICONTROL Configure]** und überprüfen Sie den Tier-Preis.

<u>Erwartete Ergebnisse</u>:

Alle zuvor konfigurierten Tier-Preise für verschiedene Websites sind vorhanden.

<u>Tatsächliche Ergebnisse</u>:

Zuvor konfigurierte Statuspreise sind nicht vorhanden.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
