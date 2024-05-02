---
title: "ACSD-51683: Die anpassbare Option kann nicht mit GraphQL zum Warenkorb hinzugefügt werden."
description: Wenden Sie den Patch ACSD-51683 an, um das Adobe Commerce-Problem zu beheben, bei dem die anpassbare Option nicht mit GraphQL zum Warenkorb hinzugefügt werden kann.
feature: GraphQL
role: Admin
exl-id: 4de0d8b7-714e-4bbf-8a0d-bb6e0c3aae55
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-51683: Die anpassbare Option kann nicht mit GraphQL zum Warenkorb hinzugefügt werden

Der Patch ACSD-51683 behebt das Problem, dass die anpassbare Option nicht mit GraphQL zum Warenkorb hinzugefügt werden kann. Dieser Patch ist verfügbar, wenn die Variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35 installiert ist. Die Patch-ID ist ACSD-51683. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] veröffentlicht. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die anpassbare Option kann nicht mit GraphQL zum Warenkorb hinzugefügt werden.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen eines einfachen Produkts mit einer anpassbaren **Textfeld** -Option.
1. [Zum Warenkorb hinzufügen](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/add-product-to-cart/) das erstellte Produkt mit der erforderlichen anpassbaren Option über GraphQL.
1. Senden Sie die [Warenkorb](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/queries/cart/) GraphQL fordert Sie auf, das Produkt und seine Details im Warenkorb zu überprüfen.

<u>Erwartete Ergebnisse</u>

Die `Customizable_options` in der GraphQL-Antwort enthält die Daten, die beim Hinzufügen des Produkts zum Warenkorb bereitgestellt werden.

<u>Tatsächliche Ergebnisse</u>

Die `Customizable_options` in der GraphQL-Antwort leer ist.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool] Handbuch.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Commerce on Cloud Infrastructure-Handbuch.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool], siehe:

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe von , ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist. [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] Handbuch.
