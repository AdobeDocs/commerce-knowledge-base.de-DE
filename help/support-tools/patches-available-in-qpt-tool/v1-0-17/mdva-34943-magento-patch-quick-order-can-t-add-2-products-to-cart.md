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

Der Patch MDVA-34943 löst das Problem, dass eine schnelle Bestellung nicht zwei oder mehr Produkte zum Warenkorb hinzufügen kann. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 ist installiert. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.4.0-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.3.0 - 2.4.1-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Benutzer können dem Warenkorb nicht in kurzer Reihenfolge zwei oder mehr Produkte hinzufügen.

<u>Voraussetzungen</u>:

Adobe Commerce mit einfachen Produkten.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu **Schnellbestellung** auf der Storefront (während nicht angemeldet).
1. Geben Sie eine gültige SKU ein, klicken Sie auf das Produkt, das im Feld für die automatische Vervollständigung angezeigt wird, und legen Sie **Menge** = *1*.
1. Geben Sie dieselbe gültige SKU ein, ändern Sie jedoch die Groß-/Kleinschreibung (ändern Sie Großbuchstaben in Kleinbuchstaben oder ändern Sie Kleinbuchstaben in Großbuchstaben) des ersten Zeichens, klicken Sie auf das Produkt, das im Feld für die automatische Vervollständigung angezeigt wird, und legen Sie **Menge** = *1*.
1. Geben Sie einen `random_sting_value` für **SKU** und legen **Menge** = *1*.
1. Satz **SKU** = *123123123* und legen **Menge** = *1*.
1. Alles mit Ausnahme des ersten Eintrags, den Sie zum **Schnellbestellung** Seite.
1. Geben Sie die erste SKU (ähnlich wie in Schritt 2) in die **Mehrere SKUs eingeben** und klicken Sie auf **Zu Liste hinzufügen**.
1. Dies ergibt eine Menge von 2 für die erste SKU und eine Zeile für eine `random_sting_value`.
1. Um mehr zu testen, aktualisieren Sie die Seite.
1. Dies führt dazu, dass keine SKUs für eine schnelle Bestellung wie erwartet verfügbar sind.
1. Geben Sie einen `random_sting_value2` in **Mehrere SKUs eingeben** und klicken Sie auf **Zu Liste hinzufügen**.
1. Dies führt zu zwei gültigen SKUs aus dem Vorfeld und einer `random_sting_value2`.

<u>Erwartete Ergebnisse</u>:

Zwei oder mehr Produkte können erwartungsgemäß zum Warenkorb hinzugefügt werden.

<u>Tatsächliche Ergebnisse</u>:

Wenn Sie zur **Warenkorb** Seite, wird das erste hinzugefügte Produkt normal angezeigt, aber für das zweite Produkt und alle nachfolgenden Produkte, die zum Warenkorb hinzugefügt werden, wird ein &quot;*1 Produkt erfordert Aufmerksamkeit*&quot; wird eine Fehlermeldung angezeigt. Das zweite oder alle weiteren Produkte werden im **Produkt erfordert Aufmerksamkeit** Abschnitt **Warenkorb** Seite.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) Abschnitt.
