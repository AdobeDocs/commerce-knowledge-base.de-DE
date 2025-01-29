---
title: Migration der Integration der Versandmethode von der SOAP zur RESTful-API [!DNL FedEx]
promoted: true
description: Patch für die Migration der Versandmethode  [!DNL FedEx]  der SOAP zur RESTful-API für Adobe Commerce 2.4.4-p4-2.4.6-pX anwenden.
feature: Shipping/Delivery
role: Developer
exl-id: 7e11a171-6924-41d0-a5c7-7b794d0da84c
source-git-commit: 7a54e992e365238ec7c764225a31cd3b6b8ad019
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# Migration der Integration der Versandmethode von der SOAP zur RESTful-API [!DNL FedEx]

>[!WARNING]
>
>Verwenden Sie den ACSD-61622 Patch der Version [!DNL Quality Patches Tool] (QPT) 1.1.57 anstelle des zuvor bereitgestellten Patches. Der neue Patch ist kompatibel mit den Adobe Commerce-Versionen (alle Bereitstellungsmethoden) 2.4.6-p1 - 2.4.6-p8. Dies könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten.
>
>Weitere Informationen finden Sie im Patch[Artikel ACSD-61622](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-57/acsd-61622-fedex-account-specific-rates-missing-from-response) in unserem Adobe Commerce-Tool-Handbuch.

>[!WARNING]
>
>Vor der Installation des neuen Patches müssen Sie den vorherigen Patch deinstallieren, der in diesem Artikel bereitgestellt wird. Anweisungen zum Deinstallieren von Patches finden Sie unter [Wiederherstellen eines benutzerdefinierten Patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches#revert-a-custom-patch) in unserem Benutzerhandbuch.


Dieser Artikel enthält einen Patch zur Behebung von Problemen mit der Migration der [!DNL FedEx] Versandmethodenintegration von SOAP zur RESTful-API für Adobe Commerce 2.4.4-p4 - 2.4.6-pX.

[!DNL FedEx Web Services] Tracking, Adressvalidierung und Validieren von Postleitzahlen Web Services Definition Languages (WSDLS) wurde am 15. Mai 2024 eingestellt. Die SOAP-basierte [!DNL FedEx Web Services] befindet sich in der Entwicklungsbeschränkung und wurde durch [!DNL FedEx] RESTFUL-APIs ersetzt. Weitere Informationen finden Sie unter [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

Diese Änderung wirkt sich auf unsere aktuelle Implementierung der [!DNL FedEx] Versandmethode in Adobe Commerce aus und erfordert, dass wir unsere aktuelle Implementierung korrigieren und von veralteten SOAP-APIs zu den neuesten [!DNL FedEx] RESTFUL-APIs migrieren.

Ab dem 15. Mai 2024 können Adobe Commerce-Kunden unsere aktuelle [!DNL FedEx] Versandmethodenintegration nicht mehr verwenden. Daher veröffentlicht Adobe diesen Hotfix, der es Kunden von Adobe Commerce 2.4.4 oder höher ermöglicht, die neuesten [!DNL FedEx] RESTFUL-APIs anstelle der veralteten SOAP-APIs zu verwenden.


## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur und On-Premise und Magento Open Source:

* 2.4.4-p4
* 2,4,5
* 2,4,5-pX
* 2,4,6
* 2.4.6-pX

## Ursache

Die [!DNL FedEx] haben ihre SOAP-basierten APIs veraltet und stattdessen durch die RESTful-APIs ersetzt. Siehe [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

## Lösung

Verwenden Sie je nach Adobe Commerce-/Magento Open Source-Version die folgenden angehängten Patches:

Um das Problem in den Versionen 2.4.4+, 2.4.5+ und 2.4.6+ zu beheben, müssen Sie den entsprechenden Patch auf Ihre Version von Adobe Commerce/Magento Open Source unten anwenden.

## Fleck

Verwenden Sie je nach Adobe Commerce-/Magento Open Source-Version die folgenden angehängten Patches:

### Für die Versionen 2.4.4-p4:

* [FedexPatch-Composer-245p5-244p6develop.patch.zip](assets/FedexPatch-Composer-245p5-244p6develop.patch.zip)

### Für die Versionen 2.4.5, 2.4.5-pX:

* [FedexPatch-Composer-245p5-244p6develop.patch.zip](assets/FedexPatch-Composer-245p5-244p6develop.patch.zip)


### Für die Versionen 2.4.6, 2.4.6-pX:


* [FedexPatch-Composer-246p3develop.patch.zip](assets/FedexPatch-Composer-246p3develop.patch.zip)


## Anbringen des Pflasters

Entpacken Sie die Datei und [ Sie in unserer Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html)Wissensdatenbank die Anleitung „So wenden Sie einen Composer-Patch von Adobe an“.

## Wie man feststellt, ob die Patches angewendet wurden

Da es nicht einfach möglich ist, zu überprüfen, ob das Problem behoben wurde, sollten Sie überprüfen, ob der Patch erfolgreich angewendet wurde. Hierbei wird (Beispiel: *AC-9363*) als zu überprüfender Patch verwendet.

<u>Sie können dies tun, indem Sie die folgenden Schritte ausführen</u>:

1. [Installieren Sie  [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Führen Sie den Befehl aus:

   ```bash
   vendor/bin/magento-patches -n status |grep "9363|Status"
   ```

1. Es sollte eine ähnliche Ausgabe angezeigt werden, bei der AC-9363 den Status *Angewendet* zurückgibt:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9363_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
