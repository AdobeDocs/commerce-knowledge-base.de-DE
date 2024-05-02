---
title: '"ACSD-53176: Produktregel mit der Bedingung "ist eins von" stimmt nicht überein."'
description: Wenden Sie den Patch ACSD-53176 an, um das Adobe Commerce-Problem zu beheben, bei dem die zugehörige Produktregel "ist eine von"-Bedingung für "Produkte, die übereinstimmen"nicht richtig funktioniert.
feature: Marketing Tools
role: Admin
exl-id: 91f05f5b-6a5e-4b93-9dfb-88cbeccb6c9e
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ACSD-53176: Produktregel mit `is one of` Bedingung stimmt nicht überein

Der Patch ACSD-53176 behebt das Problem, bei dem die zugehörige Produktregel `is one of` -Bedingung funktioniert nicht ordnungsgemäß für **Zu vergleichende Produkte**. Dieser Patch ist verfügbar, wenn die Variable [!DNL Quality Patches Tool (QPT)] 1.1.36 installiert ist. Die Patch-ID ist ACSD-53176. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.5 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die zugehörige Produktregel `is one of` -Bedingung funktioniert nicht ordnungsgemäß für **Zu vergleichende Produkte**.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie 3 bis 4 Produkte.
1. Erstellen Sie eine neue verwandte Produktregel.

   Legen Sie die Regel so fest, dass sie mit zwei oder mehr Produkten übereinstimmt:
   * `SKU is one of "S1,S2".`

   Legen Sie die Regel fest, um zwei oder mehr Elemente anzuzeigen:
   * `Product SKU is one of constant value "S2,S3".`

1. Öffnen Sie das S1-Produkt in der Storefront.

<u>Erwartete Ergebnisse</u>:

Die verwandten Produkte &quot;S2&quot;und &quot;S3&quot;werden auf beiden Produktseiten &quot;S1&quot;und &quot;S2&quot;angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Zugehörige Produkte werden nicht auf den Produktseiten angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
