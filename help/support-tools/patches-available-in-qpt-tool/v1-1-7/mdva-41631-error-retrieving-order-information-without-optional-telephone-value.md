---
title: '"MDVA-41631: Fehler beim Abrufen von Bestellinformationen ohne optionalen "Telefonwert"-Wert'
description: Der Patch MDVA-41631 behebt das Problem, dass Benutzer einen Fehler beim Abrufen von Bestellinformationen ohne optionalen "Telefonwert"über GraphQL erhalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
exl-id: 94b0b918-c1f9-4f5d-8fcd-8b92a9ca8c59
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-41631: Fehler beim Abrufen von Bestellinformationen ohne optionalen &quot;Telefonwert&quot;-Wert

Der Patch MDVA-41631 behebt das Problem, dass Benutzer einen Fehler beim Abrufen von Bestellinformationen ohne optionalen &quot;Telefonwert&quot;über GraphQL erhalten. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 ist installiert. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Benutzer erhalten einen Fehler beim Abrufen von Bestellinformationen ohne optionalen Telefonwert über GraphQL.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **Store** > **Konfiguration** > **Kunden** > **Kundenkonfiguration** > **Name und Adressenoptionen** > **Telefon anzeigen** und legen Sie die Telefonnummer als optional fest.
1. Platzieren Sie eine Bestellung mithilfe der GraphQL-API als angemeldeter Kunde.
   * Legen Sie die Telefonnummer nicht fest, wenn Sie die Abrechnungs- und Versandadressen festlegen. Befolgen Sie die Anweisungen unter [Tutorial zu GraphQL Checkout](https://devdocs.magento.com/guides/v2.4/graphql/tutorials/checkout/checkout-customer.html) in unserer Entwicklerdokumentation.
1. Abrufen der Bestellung mit der GraphQL [customerOrders-Abfrage](https://devdocs.magento.com/guides/v2.4/graphql/queries/customer-orders.html).

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

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
