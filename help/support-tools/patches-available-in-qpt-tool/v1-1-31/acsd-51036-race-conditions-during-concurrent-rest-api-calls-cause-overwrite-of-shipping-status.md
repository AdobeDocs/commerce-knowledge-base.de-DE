---
title: "ACSD-51036: Wettlaufsituationen bei gleichzeitigen REST-API-Aufrufen führen zu einer Überschreiben des Versandstatus"
description: Wenden Sie den Patch ACSD-51036 an, um das Adobe Commerce-Problem zu beheben, bei dem es bei gleichzeitigen REST-API-Aufrufen zu Race-Bedingungen kommt, was zu einer Überschreiben des Versandstatus in der bestellten Tabelle führt.
exl-id: 12d90de7-fe5c-4fcc-b84a-d420dcd871ca
feature: REST, Orders, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-51036: Wettlaufsituationen bei gleichzeitigen REST-API-Aufrufen führen zu einer Überschreiben des Versandstatus in der bestellten Tabelle

Der Patch ACSD-51036 behebt das Problem, dass die Wettlaufbedingungen bei gleichzeitigen REST-API-Aufrufen dazu führen, dass der Versandstatus in der bestellten Tabelle überschrieben wird. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.31 installiert ist. Die Patch-ID ist ACSD-51036. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Wettlaufsituationen bei gleichzeitigen REST-API-Aufrufen führen dazu, dass der Versandstatus in der bestellten Tabelle der Artikel überschrieben wird.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine Bestellung mit zwei Elementen.
1. Rechnungselement A.
1. Senden Sie gleichzeitig eine Rückerstattungsanforderung für den Artikel A über die REST-API, während Sie eine Anfrage für den Posten B senden.
1. Gehen Sie zur Bestellung in **[!UICONTROL Admin Panel]**.

<u>Erwartete Ergebnisse</u>

*[!UICONTROL Shipped 1]* Der Status sollte für Element B im *[!UICONTROL Items]* geordneter Tisch.

<u>Tatsächliche Ergebnisse</u>

*[!UICONTROL Shipped 1]* Der Status ist für Element B im *[!UICONTROL Items]* geordneter Tisch.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
