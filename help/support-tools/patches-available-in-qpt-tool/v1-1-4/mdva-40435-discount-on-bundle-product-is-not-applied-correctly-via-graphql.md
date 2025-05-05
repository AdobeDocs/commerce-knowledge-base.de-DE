---
title: 'MDVA-40435: Rabatt auf Paketprodukt wird nicht korrekt über GraphQL angewendet'
description: Der MDVA-40435 Patch löst das Problem, dass der Rabatt auf ein gebündeltes Produkt nicht korrekt über GraphQL angewendet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-40435. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
exl-id: 939ba940-35b5-4ab0-81fe-38981246e389
feature: GraphQL, Orders, Personalization, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# MDVA-40435: Rabatt auf Paketprodukt wird nicht korrekt über GraphQL angewendet

Der MDVA-40435 Patch löst das Problem, dass der Rabatt auf ein gebündeltes Produkt nicht korrekt über GraphQL angewendet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-40435. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Rabatt auf ein gebündeltes Produkt wird nicht korrekt über GraphQL angewendet.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine Warenkorb-Preisregel mit einem Gutscheincode für einen festen Rabatt von 5 USD.
1. Erstellen Sie einen leeren Warenkorb über GraphQL.
1. Fügen Sie über GraphQL ein gebündeltes Produkt zum Warenkorb hinzu.
1. Wenden Sie den Gutscheincode über GraphQL auf den Festbetrag (5$) an.
1. Rufen Sie die Warenkorbinformationen über GraphQL ab.

<u>Erwartete Ergebnisse</u>:

„Rabatte“ ist $5.

<u>Tatsächliche Ergebnisse</u>:

„Rabatte“ ist NULL.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
