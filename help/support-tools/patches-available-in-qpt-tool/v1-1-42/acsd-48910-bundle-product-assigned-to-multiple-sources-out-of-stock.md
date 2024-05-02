---
title: "ACSD-48910: Gebündeltes Produkt, dem mehrere Quellen zugewiesen sind, wird nach Rechnung und Versand aus dem Lager genommen."
description: Wenden Sie den Patch ACSD-48910 an, um das Adobe Commerce-Problem zu beheben, bei dem das gebündelte Produkt, das mehreren Quellen zugeordnet ist, nach dem Fakturieren und Versand einer Bestellung nicht mehr vorrätig ist, selbst wenn die Menge noch immer nicht null ist.
feature: Products, Inventory
role: Admin, Developer
exl-id: 6ac3dedf-1c28-4874-b963-44a429b37983
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-48910: Gebündeltes Produkt, dem mehrere Quellen zugewiesen sind, wird nach der Rechnung und dem Versand aus dem Lager geworfen

Der Patch ACSD-48910 behebt das Problem, dass das gebündelte Produkt, das mehreren Quellen zugeordnet ist, nach der Fakturierung und dem Versand einer Bestellung nicht mehr vorrätig ist, auch wenn es noch eine Menge ungleich null hat. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 ist installiert. Die Patch-ID lautet ACSD-48910. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das gebündelte Produkt, das mehreren Quellen zugeordnet ist, wird nach Rechnungsstellung und Versand nicht mehr vorrätig, auch wenn es noch verfügbar ist.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie zwei Websites.
1. Erstellen Sie zwei Stores/Store-Ansichten (eine pro Website).
1. Erstellen Sie zwei einfache Produkte (qty = 10) und weisen Sie sie sowohl Lagern als auch Websites zu.
1. Erstellen Sie ein gebündeltes Produkt und fügen Sie es mit diesen einfachen Produkten hinzu. Weisen Sie das gebündelte Produkt beiden Websites zu.
1. Gehen Sie zur Storefront und fügen Sie das gebündelte Produkt zum Warenkorb hinzu.
1. Checken Sie aus und geben Sie die Bestellung auf.
1. Rechnungsstellung und Versand der Bestellung durch den Administrator.

<u>Erwartete Ergebnisse</u>:

Das gebündelte Produkt bleibt auf Lager, da wir nur 1 der 10 Artikel gekauft haben.

<u>Tatsächliche Ergebnisse</u>:

Das gebündelte Produkt ändert seinen Status in nicht vorrätig.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
