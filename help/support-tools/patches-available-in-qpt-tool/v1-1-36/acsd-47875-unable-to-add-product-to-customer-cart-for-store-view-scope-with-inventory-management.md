---
title: "ACSD-47875: Kann kein Produkt zum Warenkorb hinzufügen, um den Umfang der Store-Ansicht mit Lagerbestandsverwaltung zu ermitteln"
description: Wenden Sie den Patch ACSD-47875 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Produkt von Admin für einen bestimmten Umfang mit Lagerbestandsverwaltung nicht zu einem Kundenkorb hinzugefügt werden kann.
feature: Inventory, Shopping Cart, Products
role: Admin, Developer
exl-id: fa5ecd65-704f-49bd-b3cc-3d60ff7e1dce
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-47875: Produkt kann nicht zum Warenkorb hinzugefügt werden, um den Umfang der Store-Ansicht mit Lagerbestandsverwaltung zu ermitteln.

Der Patch ACSD-47875 behebt das Problem, dass ein Produkt vom Administrator für einen bestimmten Umfang mit Lagerbestandsverwaltung nicht zu einem Kundenkorb hinzugefügt werden kann. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.36 installiert ist. Die Patch-ID ist ACSD-47875. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6 - p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Admin-Benutzer können ein Produkt nicht mit dem **[!UICONTROL Manage Shopping Cart]** in der Admin-Funktion für einen bestimmten Bereich der Store-Ansicht mit installiertem MSI.

<u>Voraussetzungen</u>:

[!DNL Adobe Commerce Inventory Management (MSI)] -Module installiert und aktiviert sind.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine Website, einen Store und eine Store-Ansicht.
1. Erstellen Sie eine zusätzliche Quelle, die keine *Standard*.
1. Erstellen Sie ein neues Lager und weisen Sie es der neuen Website und der neuen Quelle zu.
1. Erstellen Sie einen neuen Kunden für die neue Website.
1. Weisen Sie ein Produkt nur der neuen Website zu. Heben Sie die Zuweisung von der Standardwebsite auf.

   * Zuweisen der neuen Quelle und Festlegen der Menge *über 0* für die neue Quelle und *0* für die Standardquelle.

1. Navigieren Sie zu **[!UICONTROL Customer Edit]** in der Admin-Seite. Klicks **[!UICONTROL Manage Shopping Cart]**.
1. Ändern Sie den Umfang der Store-Ansicht in die neue Store-Ansicht.
1. Navigieren Sie zu **[!UICONTROL Products]** und suchen Sie nach dem Produkt.
1. Wählen Sie das Produkt aus und klicken Sie auf **[!UICONTROL Add selections to my cart]**.

<u>Erwartete Ergebnisse</u>:

Das Produkt wird dem Warenkorb hinzugefügt.

<u>Tatsächliche Ergebnisse</u>:

* Der folgende Fehler wird ausgegeben: *Das Produkt, das Sie hinzufügen möchten, ist nicht verfügbar.*
* Das Produkt wird nicht zum Warenkorb hinzugefügt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
