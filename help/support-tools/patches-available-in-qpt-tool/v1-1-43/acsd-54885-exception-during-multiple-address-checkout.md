---
title: "ACSD-54885: Ausnahme beim Checkout mehrerer Adressen, wenn sich der Administrator als Kunde anmeldet"
description: Wenden Sie den Patch ACSD-54885 an, um das Adobe Commerce-Problem zu beheben, bei dem beim Auschecken mehrerer Adressen ein Fehler auftritt, wenn der Administrator das * verwendet[!UICONTROL Login as Customer]* verwenden.
feature: Checkout
role: Admin, Developer
exl-id: 524ec96b-1465-4673-9fbe-1a9c086b7e87
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-54885: Ausnahme beim Checkout mehrerer Adressen, wenn sich ein Administrator als Kunde anmeldet

Der Patch ACSD-54885 behebt das Problem, dass beim Auschecken mehrerer Adressen ein Fehler auftritt, wenn der Administrator die *[!UICONTROL Login as Customer]* Funktionalität. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 ist installiert. Die Patch-ID lautet ACSD-54885. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Beim Auschecken mehrerer Adressen tritt ein Fehler auf, wenn der Administrator die Variable *[!UICONTROL Login as Customer]* Funktionalität.

<u>Zu reproduzierende Schritte</u>:

1. Stellen Sie sicher, dass *[!UICONTROL Login as Customer]* aktiviert ist. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configurations]** > **[!UICONTROL Advanced]** > **[!UICONTROL Admin]** > **[!UICONTROL Admin Actions]** > **[!UICONTROL Logging]** > **[!UICONTROL Login as Customer]**.
1. Erstellen Sie ein einfaches Produkt.
1. Erstellen Sie ein neues Kundenkonto mit einer Adresse.
1. Gehen Sie zum Kundenkonto im Backend:

   * Navigieren Sie zu **[!UICONTROL Account Information]** Registerkarte und legen Sie *[!UICONTROL Allow remote shopping assistance]* = *Ja*.
   * Klicks **[!UICONTROL Login as Customer]**.

1. Fügen Sie das Produkt zum Warenkorb hinzu und fahren Sie mit dem *[!UICONTROL Checkout with multiple addresses]*.
1. Aktualisieren Sie die Produktmenge.
1. Versuchen Sie, zum Warenkorb zurückzukehren.

<u>Erwartete Ergebnisse</u>:

Sie können den Warenkorb aktualisieren und den Auschecken mehrerer Adressen verwenden.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten die folgende Fehlermeldung, wenn Sie zum Warenkorb zurückkehren.

```PHP
report.CRITICAL: Error: Call to a member function getCustomer() on null in magento2ee/app/code/Magento/LoginAsCustomerLogging/Observer/LogUpdateQtyObserver.php:88
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
