---
title: "ACSD-51204: Produkt kehrt nach Erstellung des Kreditmemo nicht wieder auf Lager zurück."
description: Wenden Sie den Patch ACSD-51204 an, um das Adobe Commerce-Problem zu beheben, bei dem das Produkt nach dem Erstellen des Kreditmemo nicht wieder auf Lager ist.
feature: Orders, Products, Returns
role: Admin
exl-id: 302033bc-2ca5-40d6-b692-24ae46b21c31
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-51204: Produkt wird nach der Erstellung des Kreditprotokolls nicht wieder auf Lager

Der Patch ACSD-51204 behebt das Problem, dass das Produkt nach dem Erstellen des Kreditmemo nicht wieder vorrätig ist. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32 installiert ist. Die Patch-ID ist ACSD-51204. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das ausverkaufte Produkt wird nach der Erstellung des Kreditmemo nicht wieder vorrätig.

<u>Zu reproduzierende Schritte</u>:

1. Installieren **[!UICONTROL Adobe Commerce]** und aktivieren Sie die **[!UICONTROL Inventory Management Module]** mit Standard *source* und *stock* nur.
1. Hinzufügen einer **[!UICONTROL new product]** mit einer Menge *10*.
1. Weisen Sie das Produkt dem **[!UICONTROL default stock]**.
1. Fügen Sie das Produkt auf der Storefront zum Warenkorb hinzu und bestellen Sie eine ganze verfügbare Menge von 10.
1. Generieren Sie im Admin-Bereich eine *Rechnung* und *Verbringung* für die Bestellung.
1. Erstellen Sie eine **[!UICONTROL Credit Memo]** mit dem *Rückkehr an Lager* für alle Elemente aktiviert ist.
1. Überprüfen Sie die **[!UICONTROL Salable Quantity]** im Admin.

<u>Erwartete Ergebnisse</u>:

Die verkaufbare Menge des Erzeugnisses muss *10*.

<u>Tatsächliche Ergebnisse</u>:

Die verkaufbare Menge des Erzeugnisses bleibt als *0*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) im [!DNL Quality Patches Tool] Handbuch.
