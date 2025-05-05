---
title: 'ACSD-51683: Eine anpassbare Option kann nicht mit GraphQL zum Warenkorb hinzugefügt werden.'
description: Wenden Sie den Patch ACSD-51683 an, um das Adobe Commerce-Problem zu beheben, bei dem die anpassbare Option nicht mit GraphQL zum Warenkorb hinzugefügt werden kann.
feature: GraphQL
role: Admin
exl-id: 4de0d8b7-714e-4bbf-8a0d-bb6e0c3aae55
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-51683: Eine anpassbare Option kann nicht mit GraphQL zum Warenkorb hinzugefügt werden.

Der Patch ACSD-51683 behebt das Problem, dass die anpassbare Option nicht mit GraphQL zum Warenkorb hinzugefügt werden kann. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35 installiert ist. Die Patch-ID ist ACSD-51683. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die anpassbare Option kann nicht mit GraphQL zum Warenkorb hinzugefügt werden.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein einfaches Produkt mit einer anpassbaren Option **Textfeld**.
1. [Zum Warenkorb hinzufügen](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/add-product-to-cart/) das erstellte Produkt mit der erforderlichen anpassbaren Option über GraphQL.
1. Senden Sie die [Warenkorb](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/queries/cart/) GraphQL-Anfrage, um das Produkt und seine Details im Warenkorb zu überprüfen.

<u>Erwartete Ergebnisse</u>

Der `Customizable_options` Abschnitt in der GraphQL-Antwort enthält die Daten, die beim Hinzufügen des Produkts zum Warenkorb bereitgestellt wurden.

<u>Tatsächliche Ergebnisse</u>

Der `Customizable_options` Abschnitt in der GraphQL-Antwort ist leer.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
