---
title: "ACSD-50814: Admin-Benutzer kann kein Kreditmemo erstellen"
description: Wenden Sie den Patch ACSD-50814 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Admin-Benutzer kein Kreditmemo erstellen kann.
exl-id: bda374cf-6fb7-479f-8130-213ce3cc553e
feature: Admin Workspace, Orders, Returns
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-50814: Admin-Benutzer kann kein Kreditmemo erstellen

Der Patch ACSD-50814 behebt das Problem, dass ein Admin-Benutzer kein Kreditmemo erstellen kann. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 installiert ist. Die Patch-ID lautet ACSD-50814. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Ein Admin-Benutzer kann kein Kreditmemo erstellen.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie im Adobe Commerce Admin zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Shipping methods]** > **[!UICONTROL Free shipping]** und legen Sie **[!UICONTROL Enable free shipping]** auf *[!UICONTROL Yes]* fest.
1. Gehen Sie erneut zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]**, erweitern Sie die Berechnungseinstellungen und legen Sie Folgendes fest:
   * [!UICONTROL Shipping prices] = [!UICONTROL Including tax]
   * [!UICONTROL Enable cross border trade] = [!UICONTROL No]
1. Erweitern Sie die Anzeigeeinstellungen für den Preis und legen Sie den Wert [!UICONTROL Display shipping prices] = [!UICONTROL Including tax] fest.
1. Erweitern Sie die Anzeigeeinstellungen [!UICONTROL Orders], [!UICONTROL Invoices], [!UICONTROL Credit memo] und legen Sie [!UICONTROL Display shipping amount] = [!UICONTROL Including tax] fest.
1. Klare Zwischenspeicher.
1. Positionieren Sie eine Bestellung auf der Storefront.
1. Erstellen Sie eine Rechnung für die Bestellung im Admin.
1. Erstellen Sie ein Kreditmemo.

<u>Erwartete Ergebnisse</u>:

Das Kreditmemo wird erstellt.

<u>Tatsächliche Ergebnisse</u>:

Der folgende Fehler wird ausgegeben:

*Die Seite kann aufgrund des Fehlers nicht angezeigt werden*

```
report.CRITICAL: DivisionByZeroError: Division by zero in vendor/magento/module-sales/Model/Order/Creditmemo/Total/Tax.php:139*
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
