---
title: "ACSD-52736: [!UICONTROL Cart Price Rule] funktioniert nicht erwartungsgemäß"
description: Wenden Sie den Patch ACSD-52736 an, um das Adobe Commerce-Problem zu beheben, bei dem ein [!UICONTROL Cart Price Rule] , die die Anforderungen für konfigurierbare Produktmengen enthält, funktioniert nicht erwartungsgemäß.
feature: Shopping Cart, Products
role: Admin, Developer
exl-id: 8403b418-b197-4695-88a8-e322b18cd4ad
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-52736: [!UICONTROL Cart Price Rule] funktioniert nicht erwartungsgemäß

Der Patch ACSD-52736 behebt das Problem, bei dem ein [!UICONTROL Cart Price Rule] , die die Anforderungen für konfigurierbare Produktmengen enthält, funktioniert nicht erwartungsgemäß. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.36 installiert ist. Die Patch-ID ist ACSD-52736. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.5 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

A [!UICONTROL Cart Price Rule] , die die Anforderungen für konfigurierbare Produktmengen enthält, funktioniert nicht erwartungsgemäß.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine Warenkorbregel:
   * [!UICONTROL Apply] = Prozentsatz des Produktpreisrabatts
   * [!UICONTROL Discount Amount] = 60
   * [!UICONTROL Maximum Qty Discount is Applied to] = 1
   * [!UICONTROL Discount Qty Step (Buy X)] = 1
   * Wenden Sie die Regel nur auf die Artikel des Warenkorbs an, die den folgenden Bedingungen entsprechen: Die Menge im Warenkorb ist 1.
2. Produkt hinzufügen mit [!UICONTROL Qty] = 2, zum Warenkorb.
3. Überprüfen Sie die Warenkorbpreise.

<u>Erwartete Ergebnisse</u>:

Die Regel wird nicht angewendet, da die Menge der Produkte im Warenkorb *2*.

<u>Tatsächliche Ergebnisse</u>:

Der Rabatt wird angewendet.

<u> Zusätzliche Schritte, die nach der Patch-Installation erforderlich sind</u>:

Nach dem Anwenden des Pflasters wird die Warenkorbregel mithilfe der *Menge* -Attribut entfernt und erneut hinzugefügt werden.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
