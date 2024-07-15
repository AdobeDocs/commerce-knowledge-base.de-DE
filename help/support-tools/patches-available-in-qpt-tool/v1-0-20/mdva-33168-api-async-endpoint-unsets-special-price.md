---
title: "MDVA-33168: API async endpoint hebt Sonderpreis auf"
description: Der Patch MDVA-33168 behebt das Problem, dass durch die Verwendung des asynchronen API-Endpunkts zum Aktualisieren eines Produktattributs ein Sonderpreis aufgehoben wird.
exl-id: 4dd26215-b140-4924-8f4d-0d062e5fda2d
feature: REST, Orders, Personalization
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# MDVA-33168: Async-API-Endpunkt hebt Sonderpreis auf

Der Patch MDVA-33168 behebt das Problem, dass durch die Verwendung des asynchronen API-Endpunkts zum Aktualisieren eines Produktattributs ein Sonderpreis aufgehoben wird.

Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 installiert ist. Die Patch-ID lautet MDVA-33168. Bitte beachten Sie, dass das Problem in Adobe Commerce Version 2.4.3 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.3.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce über Cloud-Infrastruktur und Adobe Commerce vor Ort 2.3.3 - 2.4.2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie zwei Websites mit Geschäften.
1. Wechseln Sie zu **Stores > Konfigurationen > Katalog > Katalog > Preis > Katalog** und legen Sie **Preisbereich** = *Website* fest.
1. Erstellen Sie ein Produktattribut vom Typ *text-type* . Behalten Sie alle Optionen als Standard bei.
1. Fügen Sie dem standardmäßigen Attributsatz das erstellte Attribut hinzu.
1. Erstellen Sie ein einfaches Produkt zur Verwendung mit einem Bundle-Produkt.
1. Erstellen Sie ein Bundle-Produkt mit den folgenden Beispieloptionen:
   * **Produkt aktivieren** = *Ja*.
   * **Attributset** = *Default*.
   * **Produktname** = *bundle-1*.
   * **SKU** = *bundle-1*.
   * **Dynamische SKU** = *Ja*.
   * **Preis** = *$100.00*.
   * **Steuerklasse** = *steuerbare Güter*.
   * **Lagerstatus** = *in Lager*.
1. Legen Sie unter **Elemente bündeln** die folgenden Beispieloptionen fest:
   * **Ship Bundle Items** = *Zusammen*.
   * **Optionstitel** = *test*, **Eingabetyp** = *Optionsschaltflächen*, das Kontrollkästchen **Erforderlich** = *markiert*.
   * **Ist Standard** Kontrollkästchen = *deaktiviert*.
   * **Name** = *simple-100*.
   * **SKU** = *simple-100*.
   * **Preis** = *100.00*.
   * **Preistyp** = *Fest*.
   * **Standardmenge** = *1*.
   * **Benutzer definiert** Kontrollkästchen = *deaktiviert*.
1. Wechseln Sie den Umfang in den nicht standardmäßigen Store und legen Sie den Sonderpreis fest. (Beispiel: Legen Sie auf der Seite **Erweiterte Preise** den Wert **Sonderpreis** = *4%* und den Wert **Preisansicht** = *Preisbereich* fest.)
1. Aktualisieren Sie das neue Attribut nur im nicht standardmäßigen Store-Bereich, wie in diesem Beispiel:

   ```php
       PUT {{base_url}}/rest/en_au/async/V1/products/{{sku}}    {        "product": {            "custom_attributes": [                {                    "attribute_code": "text_attr",                    "value": 21                                   }            ]                    }    }
   ```

<u>Erwartete Ergebnisse</u>:

Andere Attributwerte bleiben beim erwarteten Aktualisieren eines Produktattributs mit der asynchronen Rest-API gleich.

<u>Tatsächliche Ergebnisse</u>:

Der Sonderpreis, der mit der asynchronen Rest-API unter dem Store-Bereich festgelegt wurde, wird entfernt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Handbuch für Softwareaktualisierungen > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie in der [Patches, die in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) verfügbar sind, in unserer Entwicklerdokumentation.
