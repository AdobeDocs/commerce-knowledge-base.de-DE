---
title: "MDVA-37779: Konfigurierbares Produkt kann nicht über GraphQL zum Warenkorb hinzugefügt werden"
description: Der Adobe Commerce-Patch MDVA-3779 behebt das Problem, dass es nicht möglich ist, ein konfigurierbares Produkt zum Warenkorb hinzuzufügen, wenn die Website-ID nicht mit der Store-ID übereinstimmt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24 installiert ist. Die Patch-ID ist MDVA-37779. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll. 
exl-id: 5f344896-39c3-4e17-89b8-1b987bae2968
feature: GraphQL, Configuration, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# MDVA-37779: Konfigurierbares Produkt kann nicht über GraphQL zum Warenkorb hinzugefügt werden

Der Adobe Commerce-Patch MDVA-3779 behebt das Problem, dass es nicht möglich ist, ein konfigurierbares Produkt zum Warenkorb hinzuzufügen, wenn die Website-ID nicht mit der Store-ID übereinstimmt. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24 ist installiert. Die Patch-ID ist MDVA-37779. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce in Cloud-Infrastruktur 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce On-Premise und Adobe Commerce über Cloud-Infrastruktur 2.4.2 - 2.4.2-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Es ist nicht möglich, dem Warenkorb konfigurierbare Produkte hinzuzufügen, wenn die Website-ID nicht mit der Store-ID übereinstimmt.

<u>Voraussetzungen</u>:

Sie verfügen über eine zweite Website-, Store- und Store-Ansicht, in der die Website-ID nicht mit der Store-ID übereinstimmt.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen eines leeren Warenkorbs mit GraphQl-Mutation `createEmptyCart`.
1. Versuchen Sie, mithilfe der `addConfigurableProductsToCart` Mutation.

<u>Erwartete Ergebnisse</u>:

Produkt zum Warenkorb hinzugefügt.

<u>Tatsächliche Ergebnisse</u>:

Fehler abrufen: *Das Produkt mit SKU xxxx konnte nicht zum Warenkorb hinzugefügt werden: Die Website mit der angeforderten ID 3 wurde nicht gefunden. Überprüfen Sie die Website und versuchen Sie es erneut.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.


## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) Abschnitt.
