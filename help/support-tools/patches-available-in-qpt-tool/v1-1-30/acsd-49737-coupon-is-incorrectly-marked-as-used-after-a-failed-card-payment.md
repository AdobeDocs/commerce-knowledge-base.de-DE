---
title: 'ACSD-49737: Der Gutschein wird nach einer fehlgeschlagenen Kartenzahlung fälschlicherweise als verwendet gekennzeichnet'
description: Wenden Sie den Patch ACSD-49737 an, um das Adobe Commerce-Problem zu beheben, bei dem der Coupon nach einer fehlgeschlagenen Kartenzahlung fälschlicherweise als verwendet gekennzeichnet ist.
exl-id: 77b5ec9c-3c4c-4da3-ba7e-8be3ccea04d0
feature: Orders, Payments
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-49737: Der Gutschein wird nach einer *Kartenzahlung fälschlicherweise als* verwendet“ gekennzeichnet

Mit dem Patch ACSD-49737 wird das Problem behoben, dass der Coupon nach einer fehlgeschlagenen Kartenzahlung fälschlicherweise *verwendet* gekennzeichnet wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 installiert ist. Die Patch-ID ist ACSD-49737. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1-p1 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Gutschein wird nach einer *Zahlung fälschlicherweise als* verwendet“ gekennzeichnet.

<u>Voraussetzungen</u>:

1. Konfigurieren Sie die **[!UICONTROL Braintree sandbox payment]**.
1. Stellen Sie sicher [*dass der Verbraucher*](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/message-queues/consumers.html?lang=de)sales.rule.update.coupon.usage) eingerichtet ist und ausgeführt wird.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine **[!UICONTROL Cart Price Rule]** mit automatisch generierten Gutscheincodes.
1. Melden Sie sich als Kunde an.
1. Produkt(e) zum Warenkorb hinzufügen.
1. Anwenden eines automatisch generierten Couponcodes.
1. Versuchen Sie, eine Bestellung mit einer fehlgeschlagenen Zahlung aufzugeben.
1. Überprüfen Sie die Couponnutzung im **[!UICONTROL Cart Price Rule]** auf der Registerkarte **[!UICONTROL Manage Coupon Codes]** .

<u>Erwartete Ergebnisse</u>:

Coupons sollten nicht als &quot;*&quot; gekennzeichnet werden* wenn die Zahlung fehlgeschlagen ist.

<u>Tatsächliche Ergebnisse</u>:

* Gutscheincode sagt - Verwendet: *Ja*, Verwendete Zeit: *1*
* Der Couponcode ist nur für eine einmalige Verwendung gültig.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Zusätzliche Schritte nach der Patch-Installation erforderlich

(Dieser Abschnitt ist optional. Nach der Anwendung des Patches sind möglicherweise einige Schritte erforderlich, um das Problem zu beheben.) 

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
