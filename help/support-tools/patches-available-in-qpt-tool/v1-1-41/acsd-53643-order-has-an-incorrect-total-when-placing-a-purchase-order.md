---
title: "ACSD-53643: Die Summe der Bestellungen ist bei der Bestellung nicht korrekt."
description: Wenden Sie den Patch ACSD-53643 an, um das Adobe Commerce-Problem zu beheben, bei dem die Bestellung bei der Bestellung mit deaktivierten oder nicht vorrätigen Produkten einen falschen Gesamtwert aufweist.
feature: B2B
role: Admin, Developer
exl-id: 9843e07a-8a17-401e-98bc-559df5148d34
source-git-commit: 2356ac10b05ae9f38e5c0ca90d9156b0fc405718
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# ACSD-53643: Die Gesamtsumme der Bestellungen ist bei der Bestellung nicht korrekt

Der Patch ACSD-53643 behebt das Problem, bei dem die Bestellung bei der Bestellung mit deaktivierten oder nicht vorrätigen Produkten einen falschen Gesamtwert aufweist. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41 installiert ist. Die Patch-ID ist ACSD-53643. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Bestellsumme ist falsch, wenn eine Bestellung mit deaktivierten oder nicht vorrätigen Produkten aufgegeben wird.

<u>Zu reproduzierende Schritte</u>:

1. Installieren *[!UICONTROL B2B]* und *[!UICONTROL Inventory]*.
1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B]** und **[!UICONTROL Company]** = *Ja* und **[!UICONTROL Purchase Order]** = *Ja*.
1. Löschen Sie den Konfigurationscache.
1. Erstellen Sie ein neues Unternehmen, aktivieren Sie es und aktivieren Sie *[!UICONTROL Purchase order]* für das Unternehmen.
1. Erstellen Sie einen neuen Benutzer für das Unternehmen.
1. Erstellen Sie eine *Validierungsregel* zur Genehmigung aller Bestellungen von mehr als *1 USD* durch den Unternehmensadministrator.
1. Erstellen Sie eine zusätzliche Quelle.
1. Melden Sie sich als neuer Unternehmensbenutzer an.
1. Fügen Sie zwei Produkte zum Warenkorb hinzu und geben Sie eine Bestellung auf.
1. Deaktivieren Sie das zweite Produkt.
1. Melden Sie sich als Unternehmensadministrator an.
1. Öffnen Sie die Bestellung und sehen Sie, dass die Bestellung sowohl Produkte als auch die Summe für beide Produkte enthält.
1. Validieren Sie die Bestellung.
1. Platzieren Sie die Bestellung.
1. Öffnen Sie die Bestelldetails.

<u>Erwartete Ergebnisse</u>:

* Die Bestellung kann nicht platziert werden, selbst wenn ein Produkt in der Bestellung *disabled* oder *nicht vorrätig*.
* *[!UICONTROL Place Order]* -Schaltfläche ausgeblendet ist.

<u>Tatsächliche Ergebnisse</u>:

Die aufgegebene Bestellung enthält nur das erste aktive Produkt, aber die Bestellsumme wird für beide Produkte berechnet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
