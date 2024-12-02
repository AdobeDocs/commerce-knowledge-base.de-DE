---
title: 'MDVA-41631: Fehler beim Abrufen von Bestellinformationen ohne optionalen "Telefonwert"-Wert'
description: Der Patch MDVA-41631 behebt das Problem, dass Benutzer einen Fehler beim Abrufen von Bestellinformationen ohne optionalen "Telefonwert"über GraphQL erhalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: 94b0b918-c1f9-4f5d-8fcd-8b92a9ca8c59
feature: Orders
role: Admin
source-git-commit: 77f41d6034f985794e5c5b89cc007a69858683b9
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-41631: Fehler beim Abrufen von Bestellinformationen ohne optionalen &quot;Telefonwert&quot;-Wert

Der Patch MDVA-41631 behebt das Problem, dass Benutzer einen Fehler beim Abrufen von Bestellinformationen ohne optionalen &quot;Telefonwert&quot;über GraphQL erhalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Benutzer erhalten einen Fehler beim Abrufen von Bestellinformationen ohne optionalen Telefonwert über GraphQL.

<u>Zu reproduzierende Schritte</u>:

1. Wechseln Sie zu **Store** > **Konfiguration** > **Kunden** > **Kundenkonfiguration** > **Name und Adressenoptionen** > **Telefon anzeigen** und legen Sie die Telefonnummer als optional fest.
1. Platzieren Sie eine Bestellung mithilfe der GraphQL-API als angemeldeter Kunde.
   * Legen Sie die Telefonnummer nicht fest, wenn Sie die Abrechnungs- und Versandadressen festlegen. Befolgen Sie die Anweisungen in [GraphQL Checkout-Tutorial](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) in unserer Entwicklerdokumentation.
1. Rufen Sie die Bestellung mit der GraphQL [customerOrders-Abfrage](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/orders/) ab.

<pre>
<code class="language-graphql">
{
  customer {
    firstname
    lastname
    suffix
    email

    orders(filter:{number:{eq:"000000001"}}){
        items{
          billing_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
shipping_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
        }
    }
  }
}
</code>
</pre>

<u>Erwartete Ergebnisse</u>:

Benutzer erhalten Bestellinformationen.

<u>Tatsächliche Ergebnisse</u>:

Benutzer erhalten den folgenden Fehler: *&quot;message&quot;: &quot;Interner Server-Fehler&quot;,*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches, die in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) verfügbar sind, in unserer Entwicklerdokumentation.
