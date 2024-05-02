---
title: '"ACSD 49843: Produkt-Download-Link nach der automatischen Rechnungsstellung mit [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]'''
description: Wenden Sie den Patch ACSD-49843 an, um das Adobe Commerce-Problem zu beheben, bei dem der Produkt-Download-Link nicht verfügbar ist, nachdem der bestellte Artikel automatisch von einer Online-Zahlungsmethode in Rechnung gestellt wurde, wenn [!UICONTROL Payment Action] auf [!UICONTROL Intent Sale].
feature: Catalog Management, Configuration, Invoices, Orders, Storefront
role: Admin, Developer
exl-id: 4bfa3827-a2b1-4168-a39c-99c617ee4795
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# ACSD-49843: Produkt-Download-Link nach der automatischen Rechnungsstellung mit [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]

Der Patch ACSD-49843 behebt das Problem, dass der Produkt-Download-Link nicht verfügbar ist, nachdem der bestellte Artikel automatisch von einer Online-Zahlungsmethode in Rechnung gestellt wurde, wenn [!UICONTROL Payment Action] auf [!UICONTROL Intent Sale]. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.37 installiert ist. Die Patch-ID lautet ACSD-49843. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Produkt-Download-Link ist nicht verfügbar, nachdem der bestellte Artikel von einer Online-Zahlungsmethode automatisch in Rechnung gestellt wurde, wenn [!UICONTROL Payment Action] auf [!UICONTROL Intent Sale].

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei Adobe Commerce Admin an und navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Configure Braintree]**.

   * Im [!UICONTROL Payment Action] Dropdown-Liste auswählen **[!UICONTROL Intent Sale]** und legen *[!UICONTROL Enable Card Payments]* nach *Ja*.

1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Downloadable Product Option]** > **[!UICONTROL Order Item status for Download]** und stellen Sie sicher, dass *&quot;Angemeldet&quot;*.
1. Melden Sie sich in der Storefront als Kunde an.

   * Fügen Sie alle herunterladbaren Produkte und ein einfaches Produkt zum Warenkorb hinzu.
   * Verwendung [!DNL Braintree Pay] , um die Bestellung mithilfe der Kartenoption zu platzieren.

1. Navigieren Sie zu **[!UICONTROL My Orders]** und sehen, dass die Rechnung automatisch für die Bestellung erstellt wird und dass beide Artikelstatus *&quot;Angemeldet&quot;*.
1. Navigieren Sie zu **[!UICONTROL My Downloadable Products]** und beachten Sie, dass der Download-Link noch nicht verfügbar ist.
1. Gehen Sie im Admin zu dieser Bestellung und erstellen Sie eine Sendung dafür.
1. Gehen Sie in die Storefront zu **[!UICONTROL My Downloadable Products]** und beachten Sie, dass der Download-Link jetzt verfügbar ist.

<u>Erwartete Ergebnisse</u>:

Der Downloadlink ist verfügbar, wenn der herunterladbare Produktstatus *&quot;Angemeldet&quot;*.

<u>Tatsächliche Ergebnisse</u>:

Der Downloadlink ist auch dann nicht verfügbar, wenn der herunterladbare Produktstatus *&quot;Angemeldet&quot;*. Sie ist erst verfügbar, nachdem eine Sendung für das physische Produkt erstellt wurde.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
