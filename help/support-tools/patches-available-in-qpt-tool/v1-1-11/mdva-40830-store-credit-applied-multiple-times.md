---
title: 'MDVA-40830: Speichergutschrift, die während der Bestellung mehrmals angewendet wurde'
description: Mit dem Patch MDVA-40830 wird das Problem behoben, dass bei der Auftragserteilung das Store-Guthaben mehrmals angewendet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 installiert ist. Die Patch-ID lautet MDVA-40830. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
exl-id: 218a100a-4500-4ef5-bbdb-fbbd12f2fa26
feature: Orders, Returns
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# MDVA-40830: Speichergutschrift, die während der Bestellung mehrmals angewendet wurde

Mit dem Patch MDVA-40830 wird das Problem behoben, dass bei der Auftragserteilung das Store-Guthaben mehrmals angewendet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 installiert ist. Die Patch-ID lautet MDVA-40830. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.3.7-p2, 2.4.0 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Store-Guthaben wird bei der Auftragserteilung mehrmals angewendet.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie einen Kunden und fügen Sie dem Kundenkonto eine Gutschrift hinzu.
1. Fügen Sie ein einfaches Produkt zum Warenkorb hinzu.
1. Legen Sie die Lieferadresse und Rechnungsadresse für den Warenkorb fest.
1. Überprüfen Sie die Gesamtsumme des Warenkorbs.
1. Wenden Sie mithilfe der folgenden GraphQL-Anfrage eine Store-Gutschrift auf den Warenkorb an:

<pre>
<code class="language-graphql">
mutation &lbrace;
  applyStoreCreditToCart(
    input: { cart_id: "%cartId%" }
  ) &lbrace;
    cart &lbrace;
      prices &lbrace;
        grand_total &lbrace;
          currency
          value
        &rbrace;
      &rbrace;
      applied_store_credit &lbrace;
        applied_balance &lbrace;
          currency
          value
        &rbrace;
        current_balance &lbrace;
          currency
          value
        &rbrace;
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

<u>Erwartete Ergebnisse</u>:

Der Wert von applied_store_credit wird genau angewendet, und die Gesamtsummen des Warenkorbs werden in der API-Antwort korrekt wiedergegeben.

<u>Tatsächliche Ergebnisse</u>:

Der Wert von applied_store_credit wird zweimal angewendet, was sowohl den Warenkorb als auch den Gesamtwert beeinflusst.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support-Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in unserer Entwicklerdokumentation.
