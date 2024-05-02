---
title: '"ACSD-53636: Der reguläre Preis wird nicht angezeigt unter [!UICONTROL Product Listing] page'''
description: Wenden Sie den Patch ACSD-53636 an, um das Adobe Commerce-Problem zu beheben, bei dem der reguläre Preis unter * nicht angezeigt wird.[!UICONTROL Product Listing]* Seiten für konfigurierbare Produkte mit untergeordneten Produkten mit Sonderpreisen.
feature: Catalog Management, Products
role: Admin, Developer
exl-id: 97b4eb64-92d1-4db1-8e5b-915b16115663
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-53636: Der reguläre Preis wird nicht angezeigt unter *[!UICONTROL Product Listing]* page

Der Patch ACSD-53636 behebt das Problem, bei dem der reguläre Preis nicht angezeigt wird auf *[!UICONTROL Product Listing]* Seiten für konfigurierbare Produkte mit untergeordneten Produkten mit Sonderpreisen. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 ist installiert. Die Patch-ID ist ACSD-53636. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.4-p6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der reguläre Preis wird nicht angezeigt unter *[!UICONTROL Product Listing]* Seiten für konfigurierbare Produkte mit untergeordneten Produkten mit Sonderpreisen.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich beim Administrator an und wechseln Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** und erstellen oder öffnen Sie ein konfigurierbares Produkt.
2. Öffnen Sie das untergeordnete Produkt, fügen Sie allen oder einem der untergeordneten Produkte einen Sonderpreis hinzu und speichern Sie das Produkt.
3. Öffnen Sie die **[!UICONTROL Product Detail]** Seite des konfigurierbaren Produkts. Auf den Farbfeldern des untergeordneten Produkts mit einem Sonderpreis wird die *[!UICONTROL Regular price]* abgestürzt (erwartet).
4. Öffnen Sie die **[!UICONTROL Product Listing]** Seite für das konfigurierbare Produkt mit einem Sonderpreis; beachten Sie, dass die konfigurierbaren Produktmuster-Änderungen nicht den regulären Preis anzeigen, im Gegensatz zum *[!UICONTROL Product Detail Page]* und anderen einfachen Produkten.

<u>Erwartete Ergebnisse</u>:

Im *[!UICONTROL Product Listing]* -Seite, zeigt das konfigurierbare Produkt den regulären Preis für das untergeordnete Produkt an.

<u>Tatsächliche Ergebnisse</u>:

Im *[!UICONTROL Product Listing]* -Seite, zeigt das konfigurierbare Produkt nicht den regulären Preis für das untergeordnete Produkt an.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
