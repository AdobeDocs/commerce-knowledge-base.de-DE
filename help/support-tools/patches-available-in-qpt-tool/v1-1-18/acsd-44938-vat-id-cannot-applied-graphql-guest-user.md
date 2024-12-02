---
title: 'ACSD-44938: VAT_ID kann nicht in GraphQL-Anfragen für Gastbenutzer angewendet werden'
description: Der Patch ACSD-44938 behebt das Problem, dass die VAT_ID nicht in einer GraphQL-Anfrage für einen Gastbenutzer angewendet werden kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 installiert ist. Die Patch-ID lautet ACSD-44938. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.
exl-id: 18b3dfa5-b666-491e-a067-526a53294f39
feature: Admin Workspace, GraphQL
role: Admin
source-git-commit: 77f41d6034f985794e5c5b89cc007a69858683b9
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-44938: VAT_ID kann nicht in GraphQL-Anfragen für Gastbenutzer angewendet werden

Der Patch ACSD-44938 behebt das Problem, dass die VAT_ID nicht in einer GraphQL-Anfrage für einen Gastbenutzer angewendet werden kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 installiert ist. Die Patch-ID lautet ACSD-44938. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.3 - p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Variable &quot;VAT_ID&quot;kann nicht in einer GraphQL-Anfrage für einen Gastbenutzer angewendet werden.

<u>Zu reproduzierende Schritte</u>:

1. Führen Sie die im Tutorial [GraphQL](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) in unserer Entwicklerdokumentation erwähnten Schritte aus, um einen Gastkarton zu erstellen.
1. Versuchen Sie, die VAT_ID für den Gastbenutzer anzuwenden, der GraphQL verwendet.

<u>Erwartete Ergebnisse</u>:

Die Variable &quot;VAT_ID&quot;kann auf dieselbe Weise wie bei einem registrierten Kunden angewendet werden. Siehe Artikel [createCustomerAddress mutation](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/mutations/create-address/) in unserer Entwicklerdokumentation.

<u>Tatsächliche Ergebnisse</u>:

Die Variable &quot;VAT_ID&quot;kann nicht auf einen Gastbenutzer angewendet werden, der GraphQL verwendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) verfügbar sind, in unserer Entwicklerdokumentation.
