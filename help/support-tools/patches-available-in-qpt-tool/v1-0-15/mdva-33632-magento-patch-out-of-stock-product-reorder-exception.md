---
title: "MDVA-33632 Patch: Out of stock product reorder exception"
description: Der Patch MDVA-33632 behebt das Problem, dass beim Versuch, ein nicht vorrätiges Produkt neu anzuordnen, eine Ausnahme ausgelöst wird.
exl-id: 4a970db4-a64c-49b5-8c5f-8b9c5cdd946f
feature: Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# MDVA-33632 Patch: Ausnahme für die Neuanordnung von nicht vorrätigen Produkten

Der Patch MDVA-33632 behebt das Problem, dass beim Versuch, ein nicht vorrätiges Produkt neu anzuordnen, eine Ausnahme ausgelöst wird.

Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.15 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.3 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:** Adobe Commerce in der Cloud-Infrastruktur 2.3.6

**Kompatibel mit Adobe Commerce-Versionen:** Adobe Commerce für Cloud-Infrastruktur und Adobe Commerce On-Premise 2.3.0 - 2.3.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein konfigurierbares Produkt mit einer Option (Beispiel: **Farbe** = *rot*) und legen Sie **qty** = *1* fest.
1. Erstellen Sie einen Kunden und geben Sie mit diesem Produkt eine Bestellung auf, die zu diesem Zeitpunkt **qty** = *0* wird.
1. Gehen Sie zu &quot;Admin&quot;und versuchen Sie, die vorherige Bestellung neu anzuordnen.

<u>Erwartete Ergebnisse</u>:

Der Kunde erhält &quot;*Dieses Produkt ist nicht vorrätig.*&quot;-Meldung für ein nicht vorrätiges Produkt, wie erwartet.

<u>Tatsächliche Ergebnisse</u>:

Der Kunde erhält &quot;*Dieses Produkt ist nicht vorrätig.Die Meldung* und `var/log/exception.log` enthalten eine ähnliche Ausnahme:

```php
[2020-12-09 00:17:36] report.CRITICAL: This product is out of stock. {"exception":"[object] (Magento\\Framework\\Exception\\LocalizedException(code: 0): This product is out of stock. at /vendor/magento/module-quote/Model/Quote.php:1711)"} []
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) verfügbare Patches.
