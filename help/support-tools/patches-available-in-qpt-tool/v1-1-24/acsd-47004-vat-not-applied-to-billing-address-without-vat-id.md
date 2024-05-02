---
title: "ACSD-47004: MwSt nicht auf Rechnungsadresse ohne MwSt-ID angewendet"
description: Wenden Sie den Patch ACSD-47004 an, um das Adobe Commerce-Problem zu beheben, bei dem die MwSt nicht auf eine Rechnungsadresse ohne MwSt-ID angewendet wird.
exl-id: 04706219-be1d-4d9a-a8bf-f5c24b45076d
feature: Customer Service, Shipping/Delivery, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 1%

---

# ACSD-47004: MwSt. wird nicht auf Rechnungsadresse ohne MwSt.-ID angewandt

Der Patch ACSD-47004 behebt das Problem, dass die Mehrwertsteuer nicht auf eine Rechnungsadresse ohne MwSt-ID angewendet wird. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)  1.1.24 ist installiert. Die Patch-ID ist ACSD-47004. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die MwSt wird nicht auf eine Rechnungsadresse ohne MwSt-ID erhoben.

<u>Zu reproduzierende Schritte</u>:

1. Öffnen Sie die [!UICONTROL Commerce Admin] > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Create New Account Options]** und legen Sie die **[!UICONTROL Enable Automatic Assignment to Customer Group]** nach *[!UICONTROL Yes]*.
1. Legen Sie unterschiedliche Gruppen für MwSt-ID-Überprüfungen fest. Beispiel:
   ![VAT-ID-validations](/help/support-tools/patches-available-in-qpt-tool/assets/vat-id-validations.png)
1. Registrieren Sie einen neuen Kunden.
1. Fügen Sie eine neue Standardadresse ohne Mehrwertsteuer hinzu. Beispiel:

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

1. Stellen Sie sicher, dass die Kundengruppe unverändert bleibt. [!UICONTROL General].
1. Bearbeiten Sie diese Adresse und fügen Sie eine gültige MwSt-Nummer hinzu:

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   VAT: DE329376919
   ```

1. Stellen Sie sicher, dass die Gruppe des Kunden zu [!UICONTROL Retailer].
1. Bearbeiten Sie die Adresse und entfernen Sie die MwSt.-Nummer:

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

<u>Erwartete Ergebnisse</u>:

Die Kundengruppe wird auf die Standardeinstellung [!UICONTROL General] automatisch hinzugefügt werden.

<u>Tatsächliche Ergebnisse</u>:

Die Kundengruppe wird nicht auf die Standardeinstellung [!UICONTROL General] automatisch hinzugefügt werden.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
