---
title: '"ACSD-46865: [!UICONTROL shipment] und [!UICONTROL credit memo] wird nicht aufgefüllt, wenn [!UICONTROL asynchronous indexing] ist aktiviert'''
description: Wenden Sie den Patch ACSD-46865 an, um das Adobe Commerce-Problem zu beheben, bei dem [!UICONTROL shipment] und [!UICONTROL credit memo] Raster werden nicht gefüllt, wenn [!UICONTROL asynchronous indexing] aktiviert ist.
exl-id: 056177a8-42f0-4138-8c04-5b037d25dfd0
feature: Cache, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-46865: [!UICONTROL shipment] und [!UICONTROL credit memo] wird nicht aufgefüllt, wenn [!UICONTROL asynchronous indexing] ist aktiviert

Der Patch ACSD-46865 behebt das Problem, bei dem [!UICONTROL shipment] und [!UICONTROL credit memo] Raster werden nicht gefüllt, wenn [!UICONTROL asynchronous indexing] aktiviert ist. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 ist installiert. Die Patch-ID ist ACSD-46865. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

[!UICONTROL Shipment] und [!UICONTROL credit memo] Raster werden nicht gefüllt, wenn [!UICONTROL asynchronous indexing] aktiviert ist.

<u>Zu reproduzierende Schritte</u>:

1. Im [!DNL Commerce] Admin, gehen Sie zu **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]** > **[!UICONTROL Asynchronous indexing Enable]** = *JA*.
2. Gehen Sie erneut zu **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoices]** > **[!UICONTROL Shipments]** > **[!UICONTROL Credit Memos Archiving]** > **[!UICONTROL Enable Archiving]** = *[!UICONTROL YES]*.
3. Bereinigen Sie den Konfigurationscache.
4. Platzieren Sie eine neue Gastbestellung für ein einfaches Produkt.
5. Führen Sie cron aus.
6. Öffnen Sie die Bestellung im [!UICONTROL Commerce] Admin, gehen Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Orders]** und generieren eine Rechnung und ein Kreditmemo.
7. Reihenfolge verschieben nach [!UICONTROL Archive].
8. Erstellen Sie eine weitere Bestellung für ein einfaches Produkt.
9. Führen Sie cron aus.
10. Gehen Sie zur neuen Bestellung und generieren Sie eine neue Lieferung, eine Rechnung und ein Kreditmemo.
11. Führen Sie cron aus.
12. Überprüfen Sie die [!UICONTROL shipments], [!UICONTROL invoices], und [!UICONTROL credit memo] Raster im Admin.

<u>Erwartete Ergebnisse</u>:

Neu [!UICONTROL shipment], [!UICONTROL invoice] und [!UICONTROL credit memo] angezeigt werden.

<u>Tatsächliche Ergebnisse</u>:

Neu [!UICONTROL shipment], [!UICONTROL invoice], und [!UICONTROL credit memo] nicht angezeigt werden.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
