---
title: "MDVA-37478: Teilrechnung über REST API nicht möglich"
description: Der Patch MDVA-37478 behebt das Problem, wenn Sie nicht in der Lage sind, eine Teilrechnung über die REST-API für eine Bestellung zu erstellen, die mit der Zahlungsmethode **Zahlung auf Konto** aufgegeben wurde. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 installiert ist. Die Patch-ID lautet MDVA-37478. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.3 behoben werden soll.
exl-id: 1b235baa-a188-467c-8ae5-de0836bc2caa
feature: REST, B2B, Invoices
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-37478: Teilrechnung über REST API nicht möglich

Der Patch MDVA-37478 behebt das Problem, wenn Sie nicht in der Lage sind, eine Teilrechnung über die REST-API für eine Bestellung zu erstellen, die mit der Zahlungsmethode platziert wurde. **Kontozahlung**. Dieser Patch ist verfügbar, wenn die Variable [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 ist installiert. Die Patch-ID lautet MDVA-37478. Bitte beachten Sie, dass das Problem in Adobe Commerce-Version 2.4.3 behoben werden soll.

## Betroffene Produkte und Versionen

* Der Patch wurde für Adobe Commerce in der Cloud-Infrastruktur 2.3.3-p1 entwickelt.
* Der Patch ist auch mit Adobe Commerce On-Premise und Adobe Commerce in der Cloud-Infrastruktur 2.3.0-2.3.7 kompatibel.

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie die `magento/quality-patches` auf die neueste Version zu aktualisieren und die Kompatibilität mit dem [[!DNL Quality Patches Tool]: Suchen Sie nach der Seite Patches .](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

<u>Voraussetzung</u>:

Adobe Commerce mit installiertem B2B-Modul

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren **B2B-Unternehmen**.
1. Aktivieren **Kontozahlung** Zahlungsmethode.
1. Erstellen Sie zwei einfache Produkte.
1. Erstellen Sie ein Unternehmenskonto.
1. Fügen Sie Firmengutschriften hinzu, die den Gesamtpreis von 2 erstellten Produkten überschreiten.
1. Melden Sie sich mit dem erstellten Unternehmenskonto an der Frontend-Seite an.
1. Fügen Sie die 2 erstellten Produkte zum Warenkorb hinzu und checken Sie mit dem **Kontozahlung** Zahlungsmethode.
1. Versuchen Sie, eine Teilrechnung für die über die REST-API erstellte Bestellung zu erstellen:

   ```php
   POST /rest/V1/order//invoice
   {
     "items": [
       {
         "order_item_id": 2,
         "qty": 1
       }
     ]
   }
   ```

<u>Erwartete Ergebnisse</u>:

Die Teilrechnung wird für eine Bestellung erstellt, die mithilfe der **Kontozahlung** Zahlungsmethode.

<u>Tatsächliche Ergebnisse</u>:

Der folgende Fehler wird von der REST-API zurückgegeben:

```php
{"message":"Invoice Document Validation Error(s):\nAn invoice for partial quantities cannot be issued for this order. To continue, change the specified quantity to the full quantity."}
```

## Wenden Sie den Patch an

Verwenden Sie je nach Adobe Commerce-Produkt die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Software-Aktualisierungshandbuch > Patches anwenden](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in unserer Entwicklerdokumentation.
* Adobe Commerce über Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Wissensdatenbank.
* [Überprüfen Sie mithilfe des Tools &quot;Qualitätsmuster&quot;, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in unserer Wissensdatenbank.

Weitere Informationen zu anderen im QPT-Tool verfügbaren Patches finden Sie im Abschnitt [Im QPT-Tool verfügbare Patches](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) Abschnitt.
