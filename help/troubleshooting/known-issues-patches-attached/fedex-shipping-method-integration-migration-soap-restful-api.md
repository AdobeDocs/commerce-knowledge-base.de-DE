---
title: '[!DNL FedEx] Migration der Versandmethode-Integration von SOAP zu RESTful-API'
promoted: true
description: Wenden Sie einen Patch an, um die [!DNL FedEx] Migration der Versandmethode-Integration von SOAP zu RESTful-API für Adobe Commerce 2.4.4-p4 - 2.4.6-pX.
feature: Shipping/Delivery
role: Developer
exl-id: 7e11a171-6924-41d0-a5c7-7b794d0da84c
source-git-commit: 7c468583883789a6bc6e41d1a787a356ea3205c4
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# [!DNL FedEx] Migration der Versandmethode-Integration von SOAP zu RESTful-API

Dieser Artikel enthält einen Patch zum Beheben von Problemen mit dem [!DNL FedEx] Migration der Versandmethode-Integration von SOAP zu RESTful-API für Adobe Commerce 2.4.4-p4 - 2.4.6-pX.

[!DNL FedEx Web Services] Die Webdienst-Definitionssprachen (WSDLS) für Tracking, Adressenvalidierung und Validierung von Postleitzahlen werden am 15. Mai 2024 eingestellt. SOAP-basiert [!DNL FedEx Web Services] befindet sich in der Entwicklungsumgebung und wurde durch [!DNL FedEx] RESTFUL-APIs. Weitere Informationen finden Sie unter [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

Diese Änderung wirkt sich auf unsere aktuelle [!DNL FedEx] Integration von Versandmethoden in Adobe Commerce. Dazu müssen wir unsere aktuelle Implementierung reparieren und von veralteten SOAP-APIs auf die neuesten migrieren [!DNL FedEx] RESTFUL-APIs.

Ab dem 15. Mai 2024 können Adobe Commerce-Kunden unsere aktuelle Version nicht mehr verwenden [!DNL FedEx] Integration von Versandmethoden, sodass Adobe diesen Hotfix veröffentlicht, mit dem Adobe Commerce 2.4.4+-Kunden die neueste Version verwenden können [!DNL FedEx] RESTFUL-APIs anstelle der veralteten SOAP-APIs.


## Betroffene Produkte und Versionen

Adobe Commerce über Cloud-Infrastruktur und On-Premise und Magento Open Source:

* 2.4.4-p4
* 2,4,5
* 2.4.5-pX
* 2,4,6
* 2.4.6-pX

## Ursache

Die [!DNL FedEx] veraltete ihre SOAP-basierten APIs und ersetzten sie stattdessen durch die RESTful-APIs. Siehe Abschnitt [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

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

Entpacken Sie die Datei und lesen Sie [Anwenden eines von Adobe bereitgestellten Composer-Patches](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) in unserer Support-Wissensdatenbank für Anleitungen.

## Ermitteln, ob die Patches angewendet wurden

Da es nicht einfach zu überprüfen ist, ob das Problem gepatcht wurde, sollten Sie überprüfen, ob der Patch erfolgreich angewendet wurde. Dies verwendet (Beispiel: *AC-9363*) als Patch zu überprüfen.

<u>Gehen Sie dazu wie folgt vor:</u>:

1. [Installieren Sie die [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Führen Sie den Befehl aus:

   ```bash
   vendor/bin/magento-patches -n status |grep "9363|Status"
   ```

1. Sie sollten die Ausgabe ähnlich wie hier sehen, wobei AC-9363 die *Angewandt* status:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9363_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
