---
title: '"ACSD-49502: Download-Link wurde nach nicht korrekt aktualisiert [!DNL staging] update'''
description: Wenden Sie den Patch ACSD-49502 an, um das Adobe Commerce-Problem zu beheben, bei dem der herunterladbare Link nach einem [!DNL staging] wird auf das herunterladbare Produkt angewendet.
exl-id: 9e7f0c06-4b7d-42c4-8ec7-cdeefd7e8a08
feature: Staging
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-49502: Download-Link wurde nach nicht korrekt aktualisiert [!DNL staging] update

Der Patch ACSD-49502 behebt das Problem, dass der herunterladbare Link nach einem [!DNL staging] wird auf das herunterladbare Produkt angewendet. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 ist installiert. Die Patch-ID lautet ACSD-49502. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der herunterladbare Link wird nach einer [!DNL staging] wird auf das herunterladbare Produkt angewendet.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein herunterladbares Produkt mit Links.
1. Erstellen Sie ein Kundenkonto und melden Sie sich an.
1. Fügen Sie das herunterladbare Produkt aus der Storefront in den Warenkorb.
1. Im **[!UICONTROL Admin]**, planen Sie ein neues Update für das herunterladbare Produkt und lassen Sie die geplante Aktualisierung abgeschlossen.
1. Führen Sie die Bestellung auf der Storefront aus.

<u>Erwartete Ergebnisse</u>:

Downloadbare Links werden beibehalten, wenn geplante Aktualisierungen verwendet werden, während zuvor hinzugefügte Produkte sich im Warenkorb befinden.

<u>Tatsächliche Ergebnisse</u>:

Herunterladbare Links fehlen sowohl unter dem *[!UICONTROL My Account]* ([!UICONTROL My Downloadable Products]) und Bestellansichtsseiten in der  **[!UICONTROL Admin]**.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
