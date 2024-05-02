---
title: '''ACSD-52606: Fehlermeldung angezeigt, wenn der Benutzer auf "Auftrag für Abruf benachrichtigen"klickt'
description: Wenden Sie den Patch ACSD-52606 an, um das Adobe Commerce-Problem zu beheben, bei dem beim Klicken auf ** eine Fehlermeldung angezeigt wird.[!UICONTROL Notify Order is Ready for Pickup]**.
feature: Orders, User Account
role: Admin, Developer
exl-id: c3e69eb1-90bf-46cf-9b53-110e40e0c3c1
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-52606: Fehlermeldung angezeigt, wenn der Benutzer auf &quot;Auftrag wird für Abruf bereit benachrichtigt&quot;klickt

Der Patch ACSD-52606 behebt das Problem, dass eine Fehlermeldung angezeigt wird. *Ihre Bestellung ist noch nicht bereit zur Übernahme* angezeigt wird, wenn der Benutzer auf **[!UICONTROL Notify Order is Ready for Pickup]**. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.37 installiert ist. Die Patch-ID ist ACSD-52606. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6 - p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Eine Fehlermeldung *Ihre Bestellung ist noch nicht bereit zur Übernahme* wird auf dem Bildschirm angezeigt, wenn der Benutzer auf **[!UICONTROL Notify Order is Ready for Pickup]**.

<u>Voraussetzungen</u>:

Inventarmodule werden installiert.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie eine neue Instanz.
1. Erstellen Sie eine neue Quelle und ein neues Lager.
1. Weisen Sie die neue Quelle der Standardwebsite zu.
1. Aktivieren Sie den Abholspeicherort für die neu erstellte Quelle.
1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]** und aktivieren **[!UICONTROL In-Store Delivery]**.
1. Erstellen Sie eine *Auf Lager* einfaches Produkt mit *QTY=0* für alle Bestände und *[!UICONTROL Manage Stock = No]* und weisen Sie ihn beiden Quellen zu.
1. Erstellen Sie eine Bestellung über das Frontend mit dem im vorherigen Schritt erstellten Produkt und wählen Sie *[!UICONTROL In-Store Pickup]* als Versandmethode.
1. Gehen Sie in Admin zu **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice that order]**.
1. Klicks **[!UICONTROL Notify order is ready for pickup]**.

<u>Erwartete Ergebnisse</u>:

Sie werden ohne Fehler benachrichtigt.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten die folgende Fehlermeldung: *Ihre Bestellung ist noch nicht bereit zur Übernahme*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
