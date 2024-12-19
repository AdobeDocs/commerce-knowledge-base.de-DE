---
title: 'ACSD-50336: E-Mails zu Produktwarnungen werden nicht gesendet'
description: Wenden Sie den Patch ACSD-50336 an, um das Adobe Commerce-Problem zu beheben, bei dem die Benachrichtigungs-E-Mails für das Produkt nicht gesendet werden, wenn ein Produkt wieder auf Lager ist oder der Preis geändert wird.
exl-id: 0fc51603-e74d-4ce7-9e67-42826ffbfab2
feature: Communications, Personalization, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-50336: E-Mails zu Produktwarnungen werden nicht gesendet

Mit dem Patch ACSD-50336 wird das Problem behoben, dass keine E-Mails zu Warnungen gesendet werden, wenn ein Produkt wieder auf Lager ist oder der Preis geändert wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 installiert ist. Die Patch-ID ist ACSD-50336. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p1 - 2.4.4-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

E-Mails zu Produktwarnungen werden nicht gesendet, wenn ein Produkt wieder auf Lager ist oder der Preis geändert wird.

<u>Voraussetzungen</u>:

Richten Sie Produktwarnhinweise ein, wenn ein Produkt wieder zum Lager hinzugefügt wird.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich als Kunde in der Storefront an.
1. Öffnen Sie ein nicht vorrätiges Produkt.
1. Abonnieren Sie eine Benachrichtigung, wenn das Produkt *wieder auf Lager* ist.
1. Aktualisieren Sie das Produkt von [!UICONTROL Admin] auf &quot;_auf Lager_.

<u>Erwartete Ergebnisse</u>:

Eine E-Mail-Benachrichtigung über das Produkt *das wieder auf Lager ist* wird an den Kunden gesendet.

<u>Tatsächliche Ergebnisse</u>:

Der Kunde erhält keine E-Mail-Benachrichtigung über das Produkt *wieder auf Lager*. Im Protokoll wird der folgende Fehler angezeigt:

```
report. CRITICAL: Magento\ProductAlert\Model\Mailing\ErrorEmailSender::execute(): Argument #2 ($storeId) must be of type int, string given, called in vendor/magento/module-product-alert/Model/Mailing/AlertProcessor.php on line 130 [] [] 
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
