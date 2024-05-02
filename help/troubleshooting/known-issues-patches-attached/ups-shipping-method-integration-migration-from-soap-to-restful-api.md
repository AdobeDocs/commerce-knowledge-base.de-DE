---
title: '[!DNL UPS] Migration der Versandmethode [!DNL SOAP] nach [!DNL RESTful API]'
promoted: true
description: Wenden Sie einen Patch an, um die [!DNL UPS] Migration der Versandmethode [!DNL SOAP] nach [!DNL RESTful API] für Adobe Commerce 2.4.4 - 2.4.6-pX.
feature: Shipping/Delivery
role: Developer
exl-id: 8ab5d4a8-0155-4b2c-ab67-d0bd2f949a07
source-git-commit: 7785a37e033bc2bea5b6a1509c337289e7b871cb
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# [!DNL UPS] Migration der Versandmethode [!DNL SOAP] nach [!DNL RESTful API]

>[!NOTE]
>
>Wenn Sie einen der drei Patches aus diesem Artikel vor **10. Oktober 2023** sollten Sie einen dieser Patches, die jetzt in diesem Artikel veröffentlicht werden, erneut auf Ihre Version 2.4.4+/2.4.5+/2.4.6+ von Adobe Commerce/Magento Open Source anwenden, da Sie sonst nicht in der Lage sein werden, bestimmte [!DNL UPS] Versandmethoden in **[!DNL Admin configuration]** und Sie müssen alle aktivieren lassen. Diese neuen Patches sind mit den zuvor veröffentlichten Patches kompatibel.

Dieser Artikel enthält einen Patch zum Beheben von Problemen mit dem [!DNL United Parcel Service (UPS)] Migration der Versandmethode [!DNL SOAP] nach [!DNL RESTful API] für Adobe Commerce 2.4.4 - 2.4.6-pX.

Gemäß den neuesten Aktualisierungen der [!DNL UPS API] Sicherheitsmodell, [!DNL UPS] hat eine [!DNL OAuth 2.0] Sicherheitsmodell für alle [!DNL APIs] (Weitere Informationen finden Sie unter [[!DNL UPS] Migrationshandbuch für den Schlüssel für den Zugriff auf Entwicklerportal](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914)) die allgemeine Sicherheit zu erhöhen, um Betrug zu reduzieren und die [!DNL API] Funktionen.

Diese Änderung wirkt sich auf unsere aktuelle [!DNL UPS] Implementierung der Versandmethode in Adobe Commerce und erfordert, dass wir unsere aktuelle Implementierung reparieren und von [!DNL SOAP API] der [!DNL RESTful API] Unterstützung [!DNL OAuth 2.0] Authentifizierungsprotokolle.

**Ab Juni 2024**, können Adobe Commerce-Händler nicht mit unserer aktuellen Transaktionsnachrichten handeln. [!DNL UPS] -Integration, sodass wir diesen Hotfix veröffentlichen, mit dem Händler von Adobe Commerce 2.4.4+/2.4.5+/2.4.6+ auf die neueste Version migrieren können [!DNL UPS REST APIs].

Dieses Problem wird in Adobe Commerce/Magento Open Source-Version 2.4.7 behoben und die Fehlerbehebung wird auch in der Beta-Version 2.4.7 vom Oktober 2023 enthalten sein.

## Betroffene Produkte und Versionen

Adobe Commerce über Cloud-Infrastruktur und On-Premise und Magento Open Source:

* 2,4,4
* 2.4.4-pX
* 2,4,5
* 2.4.5-pX
* 2,4,6
* 2.4.6-pX

## Ursache

Die [!DNL UPS] veröffentlicht [Sicherheitsupdate für ihre [!DNL API]](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914).

## Lösung

Verwenden Sie die folgenden angehängten Patches je nach Adobe Commerce-/Magento Open Source-Version:

Um das Problem in den Versionen 2.4.4+, 2.4.5+ und 2.4.6+ zu beheben, müssen Sie den entsprechenden Patch auf Ihre Version von Adobe Commerce/Magento Open Source unten anwenden.

## Patch

Verwenden Sie die folgenden angehängten Patches je nach Adobe Commerce-/Magento Open Source-Version:

### Für Versionen 2.4.4, 2.4.4-pX:

* [AC-9363_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip](assets/AC-9646_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip)

### Für Versionen 2.4.5, 2.4.5-pX:

* [AC-9358_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip](assets/AC-9647_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip)

### Für Versionen 2.4.6, 2.4.6-pX:

* [AC-9345_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip](assets/AC-9648_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip)

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
