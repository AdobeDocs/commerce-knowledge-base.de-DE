---
title: "ACSD-54776: Nicht aktiviert [!UICONTROL Use Default Value] und nicht standardmäßige Produktfeldwerte werden nicht für die zweite Website-, Store- und Store-Ansicht gespeichert."
description: Wenden Sie den Patch ACSD-54776 an, um das Adobe Commerce-Problem zu beheben, bei dem die Option deaktiviert ist. [!UICONTROL Use Default Value] und nicht standardmäßige Produktfeldwerte werden nicht für die zweite Website-, Store- und Store-Ansicht gespeichert.
feature: Products
role: Admin, Developer
exl-id: 5bdad804-8d7b-48b4-ba3b-c2d5387ef55e
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-54776: deaktiviert *[!UICONTROL Use Default Value]* und nicht standardmäßige Produktfeldwerte werden nicht gespeichert.

>[!NOTE]
>
>Dieser Patch ersetzt die [ACSD-51984](/help/support-tools/patches-available-in-qpt-tool/v1-1-35/acsd-51984-unchecked-used-default-value-and-non-default-product-field-values-are-not-saved.md) Patch veröffentlicht in QPT 1.1.35.

Der Patch ACSD-54776 behebt das Problem, bei dem das nicht aktivierte **[!UICONTROL Use Default Value]** und nicht standardmäßige Produktfeldwerte werden nicht für die zweite Website-, Store- und Store-Ansicht gespeichert. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.39 ist installiert. Die Patch-ID ist ACSD-54776. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.5-p4, 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Nicht aktiviert *[!UICONTROL Use Default Value]* und nicht standardmäßige Produktfeldwerte werden nicht für die zweite Website-, Store- und Store-Ansicht gespeichert.

<u>Zu reproduzierende Schritte</u>:

1. Rufen Sie das Backend auf und navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** und erstellen Sie eine neue Website-, Store- und Store-Ansicht.
1. Navigieren Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]**, erstellen Sie ein einfaches Produkt und speichern Sie es und weisen Sie das Produkt beiden Websites über das **[!UICONTROL Product in Websites]**.
1. Ändern Sie den Umfang in die neu erstellte Store-Ansicht aus Schritt 2.
1. Navigieren Sie zu **[!UICONTROL Search Engine Optimization]** und deaktivieren Sie die **[!UICONTROL Use Default Value]** Kontrollkästchen für [!UICONTROL Meta Title], [!UICONTROL Meta Keywords], und [!UICONTROL Meta Description].
1. Entfernen Sie den Text aus den Feldern: *[!UICONTROL Meta Title]*, *[!UICONTROL Meta Keywords]* und *[!UICONTROL Meta Description]* und klicken Sie auf **[!UICONTROL Save]**.
1. Navigieren Sie zu **[!UICONTROL Search Engine Optimization]** erneut.

<u>Erwartete Ergebnisse</u>

Die Werte für die Felder und Kontrollkästchen werden gespeichert.

<u>Tatsächliche Ergebnisse</u>

Die Werte für die Felder und Kontrollkästchen werden nicht gespeichert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) im [!DNL Quality Patches Tool] Handbuch.
