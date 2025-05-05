---
title: 'ACSD-44938: VAT_ID kann in GraphQL-Anfrage für Gastbenutzer nicht angewendet werden'
description: Mit dem Patch ACSD-44938 wird das Problem behoben, dass die VAT_ID in einer GraphQL-Anfrage für einen Gastbenutzer nicht angewendet werden kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 installiert ist. Die Patch-ID ist ACSD-44938. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.
exl-id: 18b3dfa5-b666-491e-a067-526a53294f39
feature: Admin Workspace, GraphQL
role: Admin
source-git-commit: 77f41d6034f985794e5c5b89cc007a69858683b9
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-44938: VAT_ID kann in GraphQL-Anfrage für Gastbenutzer nicht angewendet werden

Mit dem Patch ACSD-44938 wird das Problem behoben, dass die VAT_ID in einer GraphQL-Anfrage für einen Gastbenutzer nicht angewendet werden kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 installiert ist. Die Patch-ID ist ACSD-44938. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

VAT_ID kann nicht auf eine GraphQL-Anfrage für einen Gastbenutzer angewendet werden.

<u>Schritte zur Reproduktion</u>:

1. Befolgen Sie die Schritte, die im [GraphQL-Tutorial](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) in unserer Entwicklerdokumentation beschrieben werden, um einen Gästekarton zu erstellen.
1. Versuchen Sie, mit GraphQL eine VAT_ID für den Gastbenutzer anzuwenden.

<u>Erwartete Ergebnisse</u>:

VAT_ID kann auf die gleiche Weise angewendet werden wie für einen registrierten Kunden. Siehe [createCustomerAddress-Mutation](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/mutations/create-address/)-Artikel in unserer Entwicklerdokumentation.

<u>Tatsächliche Ergebnisse</u>:

VAT_ID kann nicht auf einen Gastbenutzer angewendet werden, der GraphQL verwendet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) in unserer Entwicklerdokumentation.
