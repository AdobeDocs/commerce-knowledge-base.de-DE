---
title: "ACSD-47079: Bestandsstatus von zusammengesetzten Erzeugnissen nicht aktualisiert, wenn sich der Lagerstatus der Teilprodukte ändert"
description: Wenden Sie den Patch ACSD-47079 an, um das Adobe Commerce-Problem zu beheben, bei dem der Lagerstatus von zusammengesetzten Produkten (Bundle, gruppiert und konfigurierbar) nicht aktualisiert wird, wenn sich der Lagerstatus von Unterprodukten über die REST-API-POST /rest/V1/inventory/source-items ändert.
exl-id: 603e4548-fb04-43b4-a033-4f2c7f665fae
feature: Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-47079: Bestandsstatus von zusammengesetzten Produkten wird nicht aktualisiert, wenn sich der Lagerstatus von Unterprodukten ändert

Der Patch ACSD-47079 behebt das Problem, dass der Lagerstatus von zusammengesetzten Produkten (Bundle, gruppiert und konfigurierbar) nicht aktualisiert wird, wenn der Status des untergeordneten Produktbestands über die REST-API-POST geändert wird. `/rest/V1/inventory/source-items`. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 ist installiert. Die Patch-ID ist ACSD-47079. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Lagerstatus von zusammengesetzten Produkten (Bundle, gruppiert und konfigurierbar) wird nicht aktualisiert, wenn der Lagerstatus des Unterprodukts über die REST-API-POST geändert wird. `/rest/V1/inventory/source-items`.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein konfigurierbares, gebündeltes und gruppiertes Produkt mit jeweils einem einfachen untergeordneten Produkt.
1. Legen Sie jeden einfachen untergeordneten Produktstatus auf **[!UICONTROL Out of Stock]** mithilfe der `source-items` API-Aufruf.
1. Überprüfen Sie nun den Lagerstatus des übergeordneten Produkts.

<u>Erwartete Ergebnisse</u>:

Der Status des übergeordneten Produkts lautet [!UICONTROL Out of Stock].

<u>Tatsächliche Ergebnisse</u>:

Der Status des übergeordneten Produkts lautet [!UICONTROL In Stock].

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
