---
title: '[!DNL FedEx] Migration der Versandmethode-Integration von SOAP zu RESTful-API'
promoted: true
description: Wenden Sie einen Patch an, um die Migration der [!DNL FedEx] Versandmethode-Integration von SOAP auf die RESTful-API für Adobe Commerce 2.4.4-p4 - 2.4.6-pX zu behandeln.
feature: Shipping/Delivery
role: Developer
exl-id: 7e11a171-6924-41d0-a5c7-7b794d0da84c
source-git-commit: 7c468583883789a6bc6e41d1a787a356ea3205c4
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# Migration der Versandmethode von der SOAP zur RESTful-API[!DNL FedEx]

Dieser Artikel enthält einen Patch zum Beheben von Problemen bei der Migration der Versandmethode von SOAP zu RESTful-API für Adobe Commerce 2.4.4-p4 - 2.4.6-pX.[!DNL FedEx]

[!DNL FedEx Web Services] tracking, Address Validation, and Validate Postal Codes Web Services Definition Languages (WSDLS) wird am 15. Mai 2024 eingestellt. Das SOAP basierte [!DNL FedEx Web Services] befindet sich in der Entwicklungseindämmung und wurde durch [!DNL FedEx] RESTFUL-APIs ersetzt. Weitere Informationen finden Sie unter [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

Diese Änderung wirkt sich auf unsere aktuelle Implementierung der Versandmethode für [!DNL FedEx] in Adobe Commerce aus und erfordert, dass wir unsere aktuelle Implementierung reparieren und von veralteten SOAP-APIs zu den neuesten [!DNL FedEx] RESTFUL-APIs migrieren.

Ab dem 15. Mai 2024 können Adobe Commerce-Kunden unsere aktuelle [!DNL FedEx] -Versandmethodenintegration nicht mehr verwenden. Adobe veröffentlicht daher diesen Hotfix, mit dem Adobe Commerce 2.4.4+-Kunden die neuesten [!DNL FedEx] RESTFUL-APIs anstelle der veralteten SOAP verwenden können.


## Betroffene Produkte und Versionen

Adobe Commerce über Cloud-Infrastruktur und On-Premise und Magento Open Source:

* 2.4.4-p4
* 2,4,5
* 2.4.5-pX
* 2,4,6
* 2.4.6-pX

## Ursache

Die [!DNL FedEx] veralteten ihre SOAP-basierten APIs und ersetzten sie stattdessen durch die RESTful-APIs. Siehe [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

## Lösung

Verwenden Sie die folgenden angehängten Patches je nach Adobe Commerce-/Magento Open Source-Version:

Um das Problem in den Versionen 2.4.4+, 2.4.5+ und 2.4.6+ zu beheben, müssen Sie den entsprechenden Patch auf Ihre Version von Adobe Commerce/Magento Open Source unten anwenden.

## Patch

Verwenden Sie die folgenden angehängten Patches je nach Adobe Commerce-/Magento Open Source-Version:

### Für Versionen 2.4.4-p4:

* [FedexPatch-Composer-245p5-244p6develop.patch.zip](assets/FedexPatch-Composer-245p5-244p6develop.patch.zip)

### Für Versionen 2.4.5, 2.4.5-pX:

* [FedexPatch-Composer-245p5-244p6develop.patch.zip](assets/FedexPatch-Composer-245p5-244p6develop.patch.zip)


### Für Versionen 2.4.6, 2.4.6-pX:


* [FedexPatch-Composer-246p3develop.patch.zip](assets/FedexPatch-Composer-246p3develop.patch.zip)


## Anwenden des Pflasters

Entpacken Sie die Datei und finden Sie Anweisungen unter [Anwenden eines von Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) bereitgestellten Composer-Patches in unserer Support-Wissensdatenbank.

## Ermitteln, ob die Patches angewendet wurden

Da es nicht einfach zu überprüfen ist, ob das Problem gepatcht wurde, sollten Sie überprüfen, ob der Patch erfolgreich angewendet wurde. Dabei wird (Beispiel: *AC-9363*) als zu prüfender Patch verwendet.

<u>Sie können dies tun, indem Sie die folgenden Schritte ausführen</u>:

1. [Installieren Sie den  [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Führen Sie den Befehl aus:

   ```bash
   vendor/bin/magento-patches -n status |grep "9363|Status"
   ```

1. Die Ausgabe sollte in etwa so angezeigt werden, bei der AC-9363 den Status *Angewandt* zurückgibt:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9363_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
