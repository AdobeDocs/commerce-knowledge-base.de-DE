---
title: "ACSD-55231: SKU bei Verwendung der Funktion für schnelle Bestellungen nicht gefunden Fehler"
description: Wenden Sie den Patch ACSD-55231 an, um das Adobe Commerce-Problem zu beheben, bei dem Sie die Fehlermeldung *'Die SKU wurde nicht im Katalog gefunden'* erhalten, wenn Sie versuchen, ein Produkt mithilfe der Funktion für schnelle Bestellungen zum Warenkorb hinzuzufügen.
feature: Products, Checkout, B2B
role: Admin, Developer
exl-id: 463c2c07-39ec-4b03-81f7-ec2f71f5af76
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# ACSD-55231: SKU konnte bei Verwendung der Funktion für schnelle Bestellungen keinen Fehler finden

Der Patch ACSD-55231 behebt das Problem, dass Sie *&quot;Die SKU wurde im Katalog nicht gefunden&quot;* Fehler beim Versuch, mithilfe der Funktion für schnelle Bestellungen ein Produkt zum Warenkorb hinzuzufügen. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 ist installiert. Die Patch-ID ist ACSD-55231. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Erste Schritte *&quot;Die SKU wurde nicht im Katalog gefunden&quot;* Fehler bei der Suche nach Produkten, die mithilfe der Funktion für schnelle Bestellungen zum Warenkorb hinzugefügt werden sollen.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie Adobe Commerce mit B2B-Modulen.
1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B Features]** und festlegen:
   * **[!UICONTROL Enable company]**: *Ja*
   * **[!UICONTROL Enable Shared Catalog]**: *Ja*
   * **[!UICONTROL Enable Quick Order]**: *Ja*
1. Speichern Sie die oben beschriebene Konfiguration.
1. Navigieren Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]** und erstellen Sie einen neuen freigegebenen Katalog.
1. Navigieren Sie zu **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** und erstellen Sie einen neuen Kunden:
   * Wählen Sie im Gruppenfeld den kürzlich erstellten freigegebenen Katalog aus und legen Sie *[!UICONTROL Allow remote shopping assistance]* nach *Ja*.
1. Einfaches Produkt mit SKU generieren *p12*, verknüpfen Sie sie mit der Kategorie . *c1* und wählen Sie dann den neu erstellten freigegebenen Katalog im [!UICONTROL Product in Shared Catalog] Abschnitt.
1. Ausführen:

   ```
   bin/magento ind:rei 
   bin/magento c:f 
   bin/magento cron:run (multiple times)
   ```

1. Aktualisieren Sie die Admin-Seite.
1. Navigieren Sie zu **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** und bearbeiten Sie den zuvor erstellten Kunden.
1. Klicks **[!UICONTROL Login as customer]**.
1. Navigieren Sie zu **[!UICONTROL Quick order]**.
1. Suchen Sie die *p12* SKU und klicken Sie auf die **[!UICONTROL Product Suggestion]**.
1. Fügen Sie dieses Produkt zum Warenkorb hinzu und geben Sie die Bestellung auf.
1. Zurück zu **[!UICONTROL Quick Order]**, suchen Sie nach SKU *p12* und klicken Sie erneut auf **[!UICONTROL Product Suggestion]**.

<u>Erwartete Ergebnisse</u>:

Sie können das Produkt mithilfe der Funktion für schnelle Bestellungen zum Warenkorb hinzufügen.

<u>Tatsächliche Ergebnisse</u>:

Sie können das Produkt nicht mithilfe der Funktion für schnelle Bestellungen zum Warenkorb hinzufügen und *&quot;Die SKU wurde im Katalog nicht gefunden&quot;* Fehler bei der Suche nach der Produkt-SKU.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
