---
title: "ACSD-49464: Rechnungen, Sendungen und Kreditkarten, die nicht aus dem Archiv zurückgezogen wurden"
description: Wenden Sie den Patch ACSD-49464 an, um das Adobe Commerce-Problem zu beheben, bei dem Rechnungen, Sendungen und Credit Memos nicht aus dem Archiv verschoben werden, wenn die orderId unterschiedlich ist.
exl-id: 845f9878-5f7e-4e58-8f8a-b02af17b3f11
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-49464: Rechnungen, Sendungen und Kreditkarten werden nicht aus dem Archiv zurückgezogen

Der Patch ACSD-49464 behebt das Problem, dass Rechnungen, Sendungen und Kreditkarten nicht aus dem Archiv zurückverschoben werden, wenn die orderId unterschiedlich ist. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 ist installiert. Die Patch-ID ist ACSD-49464. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Rechnungen, Sendungen und Credit Memos werden nicht aus dem Archiv verschoben, wenn die orderId unterschiedlich ist.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie die Archivierung von Bestellungen, Rechnungen, Sendungen und Kreditkarten.
1. Erstellen und schließen Sie eine Bestellung, einschließlich Versand, Rechnung und Kreditkarte.
1. Stellen Sie sicher, dass die Versand-, Rechnung- und Kreditnachrichten-IDs nicht mit der Bestellnummer übereinstimmen.
1. Verschieben Sie die Reihenfolge zum Archivieren.
1. Stellen Sie die archivierte Bestellung wieder her, um sie zu verwalten.
1. Prüfen Sie die Details zu Rechnung, Versand und Kreditkarte unter den entsprechenden [!UICONTROL Invoice], [!UICONTROL Shipping], und [!UICONTROL Credit Memo] Rasterseiten.

<u>Erwartete Ergebnisse</u>:

Die ursprünglichen zugehörigen Datensätze werden wiederhergestellt, wenn die Bestellung aus der Archivliste in die Auftragsverwaltung verschoben wird.

<u>Tatsächliche Ergebnisse</u>:

* Keine Datensätze für Versand-, Rechnung- und Kreditkarten, wenn alle Kennungen unterschiedlich sind.
* Wenn die Reihenfolge und die zugehörigen Datensätze dieselbe ID aufweisen, werden die Datensätze zurückgegeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
