---
title: '[!DNL UPS] Migration der Versandmethodenintegration von  [!DNL SOAP]  zu  [!DNL RESTful API]'
promoted: true
description: Patch für die Migration der Versandmethode  [!DNL UPS]  der Version 2.4.4 bis 2 [!DNL SOAP] 4.6-pX von zu  [!DNL RESTful API] für Adobe Commerce anwenden.
feature: Shipping/Delivery
role: Developer
exl-id: 8ab5d4a8-0155-4b2c-ab67-d0bd2f949a07
source-git-commit: 6694bb1e041e6285f5bd5a05a1c37b7062521f52
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# Migration der Integration der Versandmethode von [!DNL SOAP] nach [!DNL RESTful API] [!DNL UPS]

>[!NOTE]
>
>Wenn Sie vor dem 6. **2024 eines der drei Patches aus diesem Artikel hochgeladen haben**: Wenn dieses Problem auftritt, weil die [!DNL Metric System/SI] (Kilogramm und Zentimeter) nicht verwendet werden, sollten Sie eines dieser neuen, aktualisierten Patches, die jetzt in diesem Artikel veröffentlicht wurden, für Ihre Version 2.4.4+/2.4.5+/2.4.6+ von Adobe Commerce/Magento Open Source erneut anwenden, da Sie andernfalls die [!DNL Metric System/SI] von **Kilogramm** und **Zentimeter** in den [!DNL UPS] Versandmethoden in der **[!DNL Admin configuration]** nicht auswählen können. Diese neuen Patches sind mit den zuvor veröffentlichten Patches kompatibel. Dieses Problem wird in der kommenden Adobe Commerce-Version 2.4.7-p1, die für den 11. **2024 geplant ist, dauerhaft**.

>[!NOTE]
>
>Wenn Sie vor dem **10. Oktober 2023** eines der drei Patches aus diesem Artikel hochgeladen haben, sollten Sie eines dieser Patches, die jetzt in diesem Artikel veröffentlicht wurden, für Ihre Version 2.4.4+/2.4.5+/2.4.6+ von Adobe Commerce/Magento Open Source erneut anwenden, da Sie andernfalls bestimmte [!DNL UPS] Versandmethoden in der **[!DNL Admin configuration]** nicht auswählen und konfigurieren können und Sie alle aktivieren müssen. Diese neuen Patches sind mit den zuvor veröffentlichten Patches kompatibel.

Dieser Artikel enthält einen Patch zur Behebung von Problemen mit der Migration der [!DNL United Parcel Service (UPS)] Versandmethodenintegration von [!DNL SOAP] zu [!DNL RESTful API] für Adobe Commerce 2.4.4 - 2.4.6-pX.

Gemäß den neuesten Aktualisierungen des [!DNL UPS API] Sicherheitsmodells hat [!DNL UPS] ein [!DNL OAuth 2.0] Sicherheitsmodell für alle [!DNL APIs] implementiert (weitere Details finden Sie im [[!DNL UPS] Handbuch zur Migration des Zugriffsschlüssels für das Entwicklerportal](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914)), um die Gesamtsicherheit zur Betrugsreduzierung zu verbessern und erweiterte [!DNL API] bereitzustellen.

Diese Änderung wirkt sich auf unsere aktuelle Implementierung der [!DNL UPS] Versandmethode in Adobe Commerce aus und erfordert, dass wir unsere aktuelle Implementierung beheben und von [!DNL SOAP API] zur [!DNL RESTful API] migrieren, um [!DNL OAuth 2.0] Authentifizierungsprotokolle unterstützen zu können.

**Ab Juni 2024** Adobe Commerce-Händler keine Transaktionen mit unserer aktuellen [!DNL UPS]-Integration mehr durchführen. Daher veröffentlichen wir diesen Hotfix, der es Händlern von Adobe Commerce 2.4.4+/2.4.5+/2.4.6+ ermöglicht, zur neuesten [!DNL UPS REST APIs] zu migrieren.

Dieses Problem wird in Adobe Commerce/Magento Open Source Version 2.4.7 behoben und die Korrektur wird auch in die 2.4.7-Beta2-Version vom Oktober 2023 aufgenommen.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur und On-Premise und Magento Open Source:

* 2,4,4
* 2.4.4-pX
* 2,4,5
* 2,4,5-pX
* 2,4,6
* 2.4.6-pX

## Ursachen

Die [!DNL UPS] veröffentlichten ein [Sicherheits-Update für ihre [!DNL API]](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914).

Wenn Sie in der Europäischen Union (andere Ursprünge können dasselbe Problem aufweisen) wie Origin der Sendung haben, führt dies zu einem Fehler in der [!DNL UPS REST]:
&quot;*Eine Sendung darf keine KGS/IN- oder LBS/CM- oder OZS/CM-Einheit als Maßeinheit haben.*&quot;

## Lösung

Verwenden Sie je nach Adobe Commerce-/Magento Open Source-Version die folgenden angehängten Patches:

Um das Problem in den Versionen 2.4.4+, 2.4.5+ und 2.4.6+ zu beheben, müssen Sie den entsprechenden Patch auf Ihre Version von Adobe Commerce/Magento Open Source unten anwenden.

## Fleck

Verwenden Sie je nach Adobe Commerce-/Magento Open Source-Version die folgenden angehängten Patches:

### Für die Versionen 2.4.4, 2.4.4-pX:

* [AC-11984_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip](assets/AC-11984_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip)

### Für die Versionen 2.4.5, 2.4.5-pX:

* [AC-11983_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip](assets/AC-11983_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip)

### Für die Versionen 2.4.6, 2.4.6-pX:

* [AC-11916_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip](assets/AC-11916_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip)

## Anbringen des Pflasters

Entpacken Sie die Datei und [ Sie in unserer Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html?lang=de)Wissensdatenbank die Anleitung „So wenden Sie einen Composer-Patch von Adobe an“.

## Wie man feststellt, ob die Patches angewendet wurden

Da es nicht einfach möglich ist, zu überprüfen, ob das Problem behoben wurde, sollten Sie überprüfen, ob der Patch erfolgreich angewendet wurde. Hierbei wird (Beispiel: *AC-9363*) als zu überprüfender Patch verwendet.

<u>Sie können dies tun, indem Sie die folgenden Schritte ausführen</u>:

1. [Installieren Sie  [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de).
1. Führen Sie den Befehl aus:

   ```bash
   vendor/bin/magento-patches -n status |grep "9363|Status"
   ```

1. Es sollte eine ähnliche Ausgabe angezeigt werden, bei der AC-9363 den Status *Angewendet* zurückgibt:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9363_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
