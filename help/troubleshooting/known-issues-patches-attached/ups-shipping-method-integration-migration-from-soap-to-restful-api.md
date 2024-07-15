---
title: '[!DNL UPS] Integration der Versandmethode von  [!DNL SOAP] in [!DNL RESTful API]'
promoted: true
description: Wenden Sie einen Patch an, um die Migration der [!DNL UPS] Versandmethode-Integration von [!DNL SOAP] auf [!DNL RESTful API] für Adobe Commerce 2.4.4 - 2.4.6-pX zu behandeln.
feature: Shipping/Delivery
role: Developer
exl-id: 8ab5d4a8-0155-4b2c-ab67-d0bd2f949a07
source-git-commit: 6694bb1e041e6285f5bd5a05a1c37b7062521f52
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# [!DNL UPS] Migration der Versandmethode zur Integration von [!DNL SOAP] auf [!DNL RESTful API]

>[!NOTE]
>
>Wenn Sie einen der drei Patches aus diesem Artikel vor dem 6. Juni 2024 hochgeladen haben: Wenn dieses Problem auftritt, weil die [!DNL Metric System/SI] Messungen (Kilogramm und Zentimeter) nicht verwendet werden, sollten Sie einen dieser neuen, aktualisierten Patches, die jetzt in diesem Artikel veröffentlicht sind, für Ihre Version 2.4.4+/2.4.5+/2.4.6 erneut anwenden. Adobe Commerce/Magento Open Source erneut, da Sie andernfalls die [!DNL Metric System/SI] Messwerte für **Kilogramm** und **Zentimeter** nicht in den [!DNL UPS] Versandmethoden im **[!DNL Admin configuration]** auswählen können. **** Diese neuen Patches sind mit den zuvor veröffentlichten Patches kompatibel. Dieses Problem wird im Rahmen der bevorstehenden Adobe Commerce-Version 2.4.7-p1, die für den 11. Juni 2024 geplant ist, dauerhaft behoben.****

>[!NOTE]
>
>Wenn Sie einen der drei Patches aus diesem Artikel vor dem 10. Oktober 2023 hochgeladen haben, sollten Sie einen dieser Patches, die jetzt in diesem Artikel veröffentlicht sind, erneut auf Ihre Version 2.4.4+/2.4.5+/2.4.6+ von Adobe Commerce/Magento Open Source anwenden, da Sie sonst nicht in der Lage sind, bestimmte [!DNL UPS] Versandmethoden in **[!DNL Admin configuration]** auszuwählen und zu konfigurieren}, und Sie müssen alle aktivieren lassen. **** Diese neuen Patches sind mit den zuvor veröffentlichten Patches kompatibel.

Dieser Artikel enthält einen Patch zum Beheben von Problemen bei der Migration der Versandmethode von [!DNL SOAP] zu [!DNL RESTful API] für Adobe Commerce 2.4.4 - 2.4.6-pX.[!DNL United Parcel Service (UPS)]

Gemäß den neuesten Aktualisierungen des [!DNL UPS API]-Sicherheitsmodells hat [!DNL UPS] ein [!DNL OAuth 2.0] -Sicherheitsmodell für alle [!DNL APIs] implementiert (weitere Details finden Sie im [[!DNL UPS] Handbuch zur Migration des Zugriffsschlüssels für Entwicklerportal](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914)), um die Gesamtsicherheit zu erhöhen, um Betrug zu reduzieren und erweiterte [!DNL API]-Funktionen bereitzustellen.

Diese Änderung wirkt sich auf unsere aktuelle Implementierung der Versandmethode für [!DNL UPS] in Adobe Commerce aus und erfordert, dass wir unsere aktuelle Implementierung reparieren und von [!DNL SOAP API] auf [!DNL RESTful API] migrieren, um [!DNL OAuth 2.0]-Authentifizierungsprotokolle unterstützen zu können.

**Ab Juni 2024** können Adobe Commerce-Händler nicht mehr mit unserer aktuellen [!DNL UPS] -Integration interagieren. Daher veröffentlichen wir diesen Hotfix, mit dem Adobe Commerce 2.4.4+/2.4.5+/2.4.6+-Händler auf die neuesten [!DNL UPS REST APIs] migrieren können.

Dieses Problem wird in Adobe Commerce/Magento Open Source-Version 2.4.7 behoben und die Fehlerbehebung wird auch in der Beta-Version 2.4.7 vom Oktober 2023 enthalten sein.

## Betroffene Produkte und Versionen

Adobe Commerce über Cloud-Infrastruktur und On-Premise und Magento Open Source:

* 2,4,4
* 2.4.4-pX
* 2,4,5
* 2.4.5-pX
* 2,4,6
* 2.4.6-pX

## Ursachen

Die [!DNL UPS] hat ein [Sicherheits-Update für ihre  [!DNL API]](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914) veröffentlicht.

Wenn Sie über eine Europäische Union verfügen (andere Herkunft kann dasselbe Problem aufweisen) wie der Ursprung der Sendung, führt dies in der [!DNL UPS REST] -Anfrage zu einem Fehler:
&quot;*Eine Sendung darf nicht als Maßeinheit KGS/IN, LBS/CM oder OZS/CM verwendet werden.*&quot;

## Lösung

Verwenden Sie die folgenden angehängten Patches je nach Adobe Commerce-/Magento Open Source-Version:

Um das Problem in den Versionen 2.4.4+, 2.4.5+ und 2.4.6+ zu beheben, müssen Sie den entsprechenden Patch auf Ihre Version von Adobe Commerce/Magento Open Source unten anwenden.

## Patch

Verwenden Sie die folgenden angehängten Patches je nach Adobe Commerce-/Magento Open Source-Version:

### Für Versionen 2.4.4, 2.4.4-pX:

* [AC-11984_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip](assets/AC-11984_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip)

### Für Versionen 2.4.5, 2.4.5-pX:

* [AC-11983_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip](assets/AC-11983_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip)

### Für Versionen 2.4.6, 2.4.6-pX:

* [AC-11916_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip](assets/AC-11916_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip)

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
