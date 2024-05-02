---
title: '"MDVA-31399 Patch: Subtotal (inkl. Steuern) in der Bedingung der Warenkorbregel'''
description: Der Patch MDVA-31399 fügt die *Zwischensumme (inkl. Tax)* Option zu [Warenkorbpreisregel-Bedingung](https://docs.magento.com/user-guide/v2.3/marketing/price-rules-cart-create.html#step-2-describe-the-conditions), wodurch das Problem behoben wurde, dass es nicht möglich war, eine auf der Zwischensumme (inkl. Steuer). Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 installiert ist.
exl-id: ea0f4060-753a-4b0d-896b-fff54ffd1a82
feature: Marketing Tools, Orders, Shopping Cart, Taxes
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-31399 Patch: Subtotal (inkl. Steuer) in der Bedingung der Warenkorbregel

Der Patch MDVA-31399 fügt die *Zwischensumme (inkl. Steuern)* -Option [Bedingung der Warenkorbpreisregel](https://docs.magento.com/user-guide/v2.3/marketing/price-rules-cart-create.html#step-2-describe-the-conditions), wodurch das Problem behoben wurde, dass es nicht möglich war, eine auf der Zwischensumme (inkl. Steuer). Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 installiert ist.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.3.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.3.2 - 2.4.1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Es ist nicht möglich, eine auf der Zwischensumme (inkl. Steuer).

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren Sie den Produktpreis so, dass er die Steuer enthält.
1. Erstellen Sie eine Steuerregel und einen Steuersatz für 20 %.
1. Produkt erstellen mit **Preis** = *100* (dieser Preis beinhaltet die Steuer).
1. Erstellen Sie eine neue Preisregel für den Warenkorb mit einem Coupon &quot;10off&quot;, um einen fixen Rabatt von 10 USD anzuwenden, wenn die Zwischensumme diesen Bedingungen entspricht:

**Bedingungen**: *Wenn ALLE dieser Bedingungen TRUE sind:*        * **Zwischensumme** gleich oder größer als 100.*

<u>Erwartete Ergebnisse</u>:

Es besteht die Möglichkeit, eine Regel für den Einkaufswagenpreis in Teilsummen mit Coupon zu erstellen, um Rabatt auf die Teilsumme einschließlich Steuern anzuwenden.

<u>Tatsächliche Ergebnisse</u>:

In den Bedingungen für Warenkorbregeln gibt es zwei Optionen: *Zwischensumme* und *Zwischensumme (ausg. Steuern)* und unabhängig von der ausgewählten Option wird die Regel nur auf die Zwischensumme ohne Steuern angewendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in unserer Entwicklerdokumentation.
