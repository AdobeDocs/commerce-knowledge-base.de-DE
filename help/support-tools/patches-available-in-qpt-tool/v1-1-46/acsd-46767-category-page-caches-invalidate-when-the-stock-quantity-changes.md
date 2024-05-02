---
title: "ACSD-46767: [!UICONTROL Category] Seitenzwischenspeicher ungültig machen, wenn sich die Lagermenge ändert"
description: Wenden Sie den Patch ACSD-46767 an, um das Adobe Commerce-Problem zu beheben, bei dem das [!UICONTROL Category] Seitenzwischenspeicher invalidieren, wenn sich die Lagermenge ändert, selbst wenn das Produkt noch auf Lager ist.
feature: Cache, Products, Inventory
role: Admin, Developer
exl-id: 39811c03-8518-4975-a128-31537b4706c0
source-git-commit: b7e2ff7cd259963adb9a113eb8e94acdaa45ba1e
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-46767: [!UICONTROL Category] Seiten-Caches ungültig machen, wenn sich die Lagermenge ändert

Der Patch ACSD-46767 behebt das Problem, bei dem das [!UICONTROL Category] Seitenzwischenspeicher invalidieren, wenn sich die Lagermenge ändert, selbst wenn das Produkt noch auf Lager ist. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46 installiert ist. Die Patch-ID ist ACSD-46767. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5-p5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

[!UICONTROL Category] Seitenzwischenspeicher ungültig machen, wenn sich die Lagermenge ändert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie einige Produkte und fügen Sie sie derselben Kategorie hinzu.
1. Öffnen Sie die *[!UICONTROL Category]* auf der Storefront angezeigt, um sicherzustellen, dass die Seite zwischengespeichert wird.
1. Bestellung mit einem der Produkte der Kategorie aufgeben *(Die Produktmenge wird geändert, aber das Produkt ist noch auf Lager.)*.
1. Öffnen Sie die [!UICONTROL Category] erneut auf der Storefront angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Die Seite wird nicht aus dem Cache geladen. Sie wird neu generiert.

<u>Erwartete Ergebnisse</u>:

Die Seite wird aus dem Cache geladen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
