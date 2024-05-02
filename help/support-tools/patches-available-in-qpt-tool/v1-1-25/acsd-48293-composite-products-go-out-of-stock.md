---
title: "ACSD-48293: nicht vorrätige zusammengesetzte Erzeugnisse bei der Wiederbestockung ausverkaufter kindergesicherter Produkte"
description: Wenden Sie den Patch ACSD-48293 an, um das Adobe Commerce-Problem zu beheben, bei dem die zusammengesetzten Produkte nicht mehr vorrätig sind, wenn die ausverkauften untergeordneten Produkte wieder vorrätig sind.
exl-id: 74ca34fe-e015-4daf-a608-4756c8ab3558
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-48293: Nicht vorrätige zusammengesetzte Produkte bei ausverkauften, wieder aufgestockten Kinderprodukten

Der Patch ACSD-48293 behebt das Problem, dass die zusammengesetzten Produkte nicht mehr vorrätig sind, wenn die ausverkauften untergeordneten Produkte wieder vorrätig sind. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 ist installiert. Die Patch-ID lautet ACSD-48293. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Composite-Produkte werden nicht mehr vorrätig, wenn die ausverkauften Kinderprodukte wieder vorrätig sind.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine sekundäre Website-, Store- und Store-Ansicht.
1. Erstellen Sie zwei Quellen und Lager und weisen Sie sie jeder Website zu.
1. Aktivieren Sie die Option Nicht vorrätige Produkte anzeigen unter **[!UICONTROL Store]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** > **[!UICONTROL Display Out-of-Stock Products]** = *[!UICONTROL Yes]*.
1. Erstellen Sie ein konfigurierbares Produkt mit einem verknüpften Produkt mithilfe der Stammquelle der primären Website (Set qty = 1).
1. eine Bestellung für das konfigurierbare Produkt aufgeben.
1. Führen Sie den Cron aus.
1. Öffnen Sie das konfigurierbare Produkt aus der Storefront und bestätigen Sie, dass es nicht vorrätig ist.
1. Öffnen Sie das konfigurierbare Produkt über die [!UICONTROL Admin] und legen Sie die **[!UICONTROL Manage Stock Option]** nach *[!UICONTROL No]*.
1. Führen Sie den Cron aus.
1. Liefert die Bestellung und fügt dem einfachen Produkt eine Menge hinzu, damit es auf Lager ist.
1. Führen Sie den Cron aus.
1. Überprüfen Sie die Produktverfügbarkeit auf der Storefront.

<u>Erwartete Ergebnisse</u>:

Das konfigurierbare Produkt ist auf Lager.

<u>Tatsächliche Ergebnisse</u>:

Das konfigurierbare Produkt ist nicht vorrätig.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
