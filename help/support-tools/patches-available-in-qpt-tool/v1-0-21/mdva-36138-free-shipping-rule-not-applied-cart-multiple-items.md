---
title: "MDVA-36138: Freie Versandregel gilt nicht für mehrere Artikel aus dem Warenkorb"
description: Der Patch MDVA-36138 behebt das Problem, dass bei mehreren Artikeln im Warenkorb die passende SKU im Free Shipping keine kostenlose Lieferung erhält. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 installiert ist. Die Patch-ID lautet MDVA-36138. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
exl-id: 74e25ca8-e4fa-47f4-ab95-561f70e05727
feature: Orders, Shipping/Delivery, Personalization, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-36138: Kostenlose Versandregel nicht angewandt Warenkorb mehrere Artikel

Der Patch MDVA-36138 behebt das Problem, dass bei mehreren Artikeln im Warenkorb die passende SKU im Free Shipping keine kostenlose Lieferung erhält. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 installiert ist. Die Patch-ID lautet MDVA-36138. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce in Cloud-Infrastruktur 2.3.4

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.2 und höher

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn eine kostenlose Versandregel nur auf bestimmte Artikel angewendet wird, gilt der Rabatt nicht für andere Artikel im Warenkorb.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie einfache Produkte - simple1 und simple2.
1. USPS konfigurieren (oder eine beliebige Online-Versandmethode):

   * Zulässige Methoden: Priority Mail (eine Methode, die ausgewählt wurde, um keine lange Liste von Methoden im Warenkorb und Kasse zu haben).
   * Kostenlose Methode: Priority Mail.

1. Erstellen Sie eine Warenkorbregel:

   * Gutscheincode angeben
   * Registerkarte &quot;Bedingungen&quot;: leer lassen
   * Registerkarte Aktionen :

   `Condition: SKU is simple1`
   `Free Shipping: For matching items only`

1. Fügen Sie simple1 zum Warenkorb hinzu.
1. Wenden Sie den Gutscheincode an.
1. Fügen Sie simple2 zum Warenkorb hinzu.

<u>Erwartete Ergebnisse</u>:

* simple1 - sollte kostenlosen Versand haben.
* simple2 - Versand sollte bezahlt werden.

<u>Tatsächliche Ergebnisse</u>:

Der Versandpreis beinhaltet simple1 und simple2.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
