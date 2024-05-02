---
title: "ACSD-55352: Erstellen von Kreditkarten mit Bonuspunkten"
description: Wenden Sie den Patch ACSD-55352 an, um das Adobe Commerce-Problem zu beheben, bei dem nach dem Erstellen eines partiellen Kreditmemo mit Kundenbelohnungspunkten der Auftragsstatus zu *geschlossen* geändert wird und die Kreditmemo-Optionen auf der Seite "Admin-Bestellung"nicht mehr angezeigt werden.
feature: Checkout, Orders
role: Admin, Developer
exl-id: 33ceb2e9-3cd5-4472-941a-e06c5c534f4a
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# ACSD-55352: Erstellen von Kreditkarten mit Bonuspunkten

Der Patch ACSD-55352 behebt das Problem, dass sich der Auftragsstatus nach der Erstellung eines partiellen Kreditmemo mit Kundenbelohnungspunkten in *geschlossen* und die Optionen für das Credit Memo werden auf der Seite &quot;Administratorbestellung&quot;nicht mehr angezeigt. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 ist installiert. Die Patch-ID ist ACSD-55352. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Nachdem Sie ein Teil-Kreditmemo mit Kundenbelohnungspunkten erstellt haben, ändert sich der Auftragsstatus in *geschlossen* und die Optionen für das Credit Memo werden auf der Seite &quot;Administratorbestellung&quot;nicht mehr angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei Adobe Commerce Admin an.
2. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Other Setting]** > **[!UICONTROL Reward Exchange Rates]** > **[!UICONTROL Add New Rate]**.
3. Fügen Sie zwei Raten hinzu:
   * *[!UICONTROL First]*:
      * *[!UICONTROL Direction]* = *Punkte zur Währung*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
   * *[!UICONTROL Second]*:
      * *[!UICONTROL Direction]* = *Währung bis Punkt*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
4. Erstellen eines einfachen Produkts mit dem Preis von *100$* und *Qty* : *100*.
5. Erstellen Sie einen Kunden aus der Storefront.
6. Wechseln Sie erneut zum Backend : **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** > **[!UICONTROL Edit]** > **[!UICONTROL Reward Points]** > **[!UICONTROL Update Points]** > Hinzufügen *100* und speichern Sie den Kunden.
7. Gehen Sie zur Storefront und melden Sie sich als zuvor vom Kunden erstellter Kunde an.
8. Produkt zum Warenkorb hinzufügen mit *Qty* : *10*.
9. Navigieren Sie zu **[!UICONTROL Checkout]** und verwenden Sie die verfügbaren *100* belohnen Punkte, wenn Sie dazu aufgefordert werden, und platzieren Sie die Bestellung.
10. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice]** und diese Bestellung verschicken.
11. Navigieren Sie zu [!UICONTROL Credit Memo] und aktualisieren Sie *Erstattungsmenge* nach *8*.
12. Klicken Sie auf **[!UICONTROL Refund Reward Points]** aktivieren und auf **[!UICONTROL Refund offline]**.
13. Versuchen Sie, die anderen beiden verbleibenden Produkte aus der Bestellung zurückzuerstatten, indem Sie die [!UICONTROL Credit Memo].

<u>Erwartete Ergebnisse</u>:

* Der Administrator erstellt [!UICONTROL Credit Memo] um die beiden verbleibenden Produkte zurückzugeben.
* Der Bestellstatus lautet *Abgeschlossen*.

<u>Tatsächliche Ergebnisse</u>:

* Kann nicht mehr erstellen [!UICONTROL Credit Memo].
* Der Bestellstatus lautet *Geschlossen*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
