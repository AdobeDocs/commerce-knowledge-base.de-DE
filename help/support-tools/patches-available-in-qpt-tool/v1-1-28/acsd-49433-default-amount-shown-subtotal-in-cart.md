---
title: 'ACSD-49433: Standardbetrag als Zwischensumme im Warenkorb für Geschenkkarte angezeigt"'
description: Wenden Sie den Patch ACSD-49433 an, um das Adobe Commerce-Problem zu beheben, bei dem der Standardbetrag als Zwischensumme im Warenkorb für Geschenkkarten mit einem offenen Betrag angezeigt wird.
exl-id: e2a887bb-c15a-43a6-a145-b295deef399b
feature: Admin Workspace, Gift, Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-49433: Standardbetrag als Zwischensumme im Warenkorb für Geschenkkarte angezeigt

Der Patch ACSD-49433 behebt das Problem, dass der Standardbetrag als Zwischensumme im Warenkorb für die Geschenkkarte mit einem offenen Betrag angezeigt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 installiert ist. Die Patch-ID lautet ACSD-49433. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Standardbetrag wird als Zwischensumme im Warenkorb für die Geschenkkarte mit einem offenen Betrag angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine Geschenkkarte.
1. Stellen Sie sicher, dass der offene Betrag auf *[!UICONTROL Yes]* (zwischen 50 und 500 $) gesetzt ist.
1. Gehen Sie zum Produkt &quot;[!UICONTROL Gift Card]&quot;in der Storefront und wählen Sie einen anderen Betrag aus der Dropdown-Liste aus.
1. Geben Sie 100 USD in USD an.
1. Füllen Sie andere Felder aus und fügen Sie sie zum Warenkorb hinzu.
1. Gehen Sie zum Mini-Warenkorb oder zur Warenkorbseite.

<u>Erwartete Ergebnisse</u>:

Die Zwischensumme zeigt den vom Benutzer eingegebenen Betrag an.

<u>Tatsächliche Ergebnisse</u>:

In der Zwischensumme wird der standardmäßige Betrag der Geschenkkarte angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
