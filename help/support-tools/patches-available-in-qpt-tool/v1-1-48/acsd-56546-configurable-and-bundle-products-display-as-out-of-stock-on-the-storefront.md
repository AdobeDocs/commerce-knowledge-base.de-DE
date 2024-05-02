---
title: "ACSD-56546: Konfigurierbare und gebündelte Produkte werden auf der Storefront als nicht vorrätig angezeigt."
description: Wenden Sie den Patch ACSD-56546 an, um das Adobe Commerce-Problem zu beheben, bei dem die konfigurierbaren und Bundle-Produkte als nicht vorrätig auf der Storefront angezeigt werden, wenn das *[!UICONTROL Display Out of Stock Products]* Die Konfigurationsoption ist deaktiviert.
feature: Storefront, Products
role: Admin, Developer
exl-id: 488e2c69-442f-45e1-aa8f-71d9c0a93950
source-git-commit: 031d5cad6727bac61c88f21fa7c84e0d2a6df331
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-56546: Konfigurierbare und gebündelte Produkte werden auf der Storefront als nicht vorrätig angezeigt

Der Patch ACSD-56546 behebt das Problem, dass die konfigurierbaren und Bundle-Produkte auf der Storefront als nicht vorrätig angezeigt werden. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 ist installiert. Die Patch-ID ist ACSD-56546. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Konfigurierbare und gebündelte Produkte werden auf der Storefront als nicht vorrätig angezeigt, wenn *[!UICONTROL Display Out of Stock Products]* deaktiviert ist.

<u>Zu reproduzierende Schritte</u>:

1. Legen Sie die **[!UICONTROL Display Out of Stock Products]** -Option *Nein*.
1. Erstellen Sie eine Website, einen Store und einen Store.
1. Erstellen Sie eine Quelle und ein Lager und weisen Sie es der zweiten Website zu.
1. Erstellen Sie eine *konfigurierbares Produkt* mit zwei Kinderprodukten. Weisen Sie beide untergeordneten Produkte beiden Quellen und beiden Websites zu.
1. Aktualisieren Sie das erste untergeordnete Produkt, das *qty=0* in beiden Quellen.
1. Aktualisieren Sie das zweite untergeordnete Produkt und deaktivieren Sie es auf der zweiten Website.
1. Führen Sie eine vollständige Neuindizierung durch.
1. Überprüfen Sie die Kategorie, die das konfigurierbare Produkt auf der zweiten Website enthält.

<u>Erwartete Ergebnisse</u>:

Die konfigurierbaren Nicht-Lager-Produkte sind auf der Storefront nicht sichtbar.

<u>Tatsächliche Ergebnisse</u>:

Die konfigurierbaren Nicht-Lager-Produkte sind auch dann auf der Storefront sichtbar, wenn die *[!UICONTROL Display Out of Stock Products]* deaktiviert ist.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
