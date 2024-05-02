---
title: '"MDVA-37224: Unfähig, "verhandelbares Angebot"mit PayFlow Pro zu bezahlen"'
description: Der Patch MDVA-37224 behebt das Problem, dass Kunden mit Paypal PayFlow Pro kein "Negotiable Quote"zahlen können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 installiert ist. Die Patch-ID lautet MDVA-37224. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.3 behoben werden soll.
exl-id: df75b38d-64c8-46b5-85ff-7606ce1dfd34
feature: B2B, Orders, Payments, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-37224: Unfähig, &quot;verhandelbares Angebot&quot;mit PayFlow Pro zu bezahlen

Der Patch MDVA-37224 behebt das Problem, wenn Kunden für eine **Negotiatives Zitat** mit Paypal PayFlow Pro. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 ist installiert. Die Patch-ID lautet MDVA-37224. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.3 behoben werden soll.

## Betroffene Produkte und Versionen

* Der Patch wurde für Adobe Commerce in der Cloud-Infrastruktur 2.3.6-p1 entwickelt.
* Der Patch ist auch mit Adobe Commerce On-Premise und Adobe Commerce in der Cloud-Infrastruktur 2.3.3-2.4.2-p1 kompatibel

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Voraussetzungen</u>:

* Adobe Commerce mit installiertem B2B-Modul
* Aktivierung der Unternehmensfunktion
* **Negotiatives Zitat** Funktion aktiviert
* Ein Unternehmensbenutzer ist vorhanden
* PayPal PayFlow Pro Zahlungsmethode ist aktiviert und konfiguriert
* PayPal PayFlow Pro Zahlungsmethode ist für B2B zulässig
* 2 Produkte mit unterschiedlichen Preisen wurden erstellt

<u>Zu reproduzierende Schritte</u>:

1. Öffnen Sie die Storefront.
1. Hinzufügen **Produkt 1** in den Warenkorb.
1. Erstellen Sie eine **Negotiatives Zitat** für **Produkt 1**.
1. Hinzufügen **Produkt 2** in den Warenkorb.
1. Akzeptieren Sie vom Administrator aus die **Negotiatives Zitat** erstellt in Schritt 3.
1. Öffnen Sie in der Storefront diesen **Negotiatives Zitat** und fahren Sie mit dem Checkout fort.
1. Wählen Sie die **Zahlungsmethode** = *PayPal PayFlow Pro* im **Überprüfung und Zahlungen** Schritt.
1. Platzieren Sie die Bestellung.

<u>Erwartete Ergebnisse</u>:

* Die Bestellung wurde wie erwartet erfolgreich platziert.
* PayPal sendet E-Mails mit den richtigen Informationen wie erwartet an den Kunden.

<u>Tatsächliche Ergebnisse</u>:

* Die Webseite hängt und schließt die Bestellung nicht ab.
* PayPal sendet eine Bestätigung mit Nullwerten an den Kunden, ähnlich wie in diesem Beispiel:

```php
Order ID: A1xxxxxxxxx
Order Placed: Monday, April 21, 2021 01:12:12 PM PDT

Shipping Amount: $0.00
Tax Amount: $0.00
Amount of Transaction: $0.00
Payment Type: Visa

BILL TO
--------
US
```


## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* 
   * [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) Abschnitt.
