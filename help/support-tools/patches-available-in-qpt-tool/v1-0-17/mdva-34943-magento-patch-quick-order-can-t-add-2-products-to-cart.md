---
title: "MDVA-34943: Schnellbestellung kann nicht mehr als 2 Produkte zum Warenkorb hinzufügen"
description: Der Patch MDVA-34943 löst das Problem, dass eine schnelle Bestellung nicht zwei oder mehr Produkte zum Warenkorb hinzufügen kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.2 behoben wurde.
exl-id: fcff6a78-fe00-4352-b0bc-149bd411d999
feature: Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---

# MDVA-34943: Schnellbestellung kann nicht mehr als 2 Produkte zum Warenkorb hinzufügen

Der Patch MDVA-34943 löst das Problem, dass eine schnelle Bestellung nicht zwei oder mehr Produkte zum Warenkorb hinzufügen kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.4.0-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.3.0 - 2.4.1-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Benutzer können dem Warenkorb nicht in kurzer Reihenfolge zwei oder mehr Produkte hinzufügen.

<u>Voraussetzungen</u>:

Adobe Commerce mit einfachen Produkten.

<u>Zu reproduzierende Schritte</u>:

1. Wechseln Sie in der Storefront zu **Quick Order** (ohne angemeldet zu sein).
1. Geben Sie eine gültige SKU ein, klicken Sie auf das Produkt, das im Feld für die automatische Vervollständigung angezeigt wird, und legen Sie **Menge** = *1* fest.
1. Geben Sie dieselbe gültige SKU ein, ändern Sie jedoch die Groß-/Kleinschreibung des ersten Zeichens (ändern Sie Großbuchstaben in Kleinbuchstaben oder ändern Sie Kleinbuchstaben in Großbuchstaben), klicken Sie auf das Produkt, das im Feld für die automatische Vervollständigung angezeigt wird, und legen Sie **Quantity** = *1* fest.
1. Geben Sie einen `random_sting_value` für **SKU** ein und legen Sie **Quantity** = *1* fest.
1. Legen Sie **SKU** = *123123123* fest und legen Sie **Quantity** = *1* fest.
1. Löschen Sie alle Elemente außer dem ersten Eintrag, den Sie der Seite **Quick Order** hinzugefügt haben.
1. Geben Sie die erste SKU (ähnlich wie in Schritt 2 oben) in das Feld **Mehrere SKUs eingeben** ein und klicken Sie auf **Zu Liste hinzufügen**.
1. Dies ergibt eine Menge von 2 für die erste SKU und eine Zeile für eine `random_sting_value`.
1. Um mehr zu testen, aktualisieren Sie die Seite.
1. Dies führt dazu, dass keine SKUs für eine schnelle Bestellung wie erwartet verfügbar sind.
1. Geben Sie einen `random_sting_value2` in das Feld **Mehrere SKUs eingeben** ein und klicken Sie auf **Zur Liste hinzufügen**.
1. Dies führt zu zwei gültigen SKUs aus dem Vorfeld und einem `random_sting_value2`.

<u>Erwartete Ergebnisse</u>:

Zwei oder mehr Produkte können erwartungsgemäß zum Warenkorb hinzugefügt werden.

<u>Tatsächliche Ergebnisse</u>:

Wenn Sie zur Seite **Warenkorb** gehen, wird das erste hinzugefügte Produkt normal angezeigt. Für das zweite Produkt und alle nachfolgenden Produkte, die zum Warenkorb hinzugefügt werden, ist jedoch eine Fehlermeldung &quot;*1 Produkt erfordert Aufmerksamkeit*&quot; angezeigt. Das zweite oder jedes weitere Produkt wird im Abschnitt **Wichtiges Produkt** der Seite **Warenkorb** aufgelistet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) verfügbare Patches.
