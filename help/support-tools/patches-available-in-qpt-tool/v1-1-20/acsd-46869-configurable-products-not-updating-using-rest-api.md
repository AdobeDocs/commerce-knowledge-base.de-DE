---
title: 'ACSD-46869: Konfigurierbare Produkte werden beim Checkout nicht mit der REST-API aktualisiert.'
description: Mit dem Patch ACSD-46869 wird das Problem behoben, dass die konfigurierbaren Produkte beim Checkout nicht mit der REST-API aktualisiert werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 installiert ist. Die Patch-ID ist ACSD-46869. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.
exl-id: d1bac489-f0f3-4b50-bc48-86c844230da7
feature: REST, Checkout, Configuration, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-46869: Konfigurierbare Produkte werden beim Checkout nicht mit der REST-API aktualisiert.

Mit dem Patch ACSD-46869 wird das Problem behoben, dass konfigurierbare Produkte beim Checkout nicht mit der REST-API aktualisiert werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 installiert ist. Die Patch-ID ist ACSD-46869. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der [[!DNL QPT] Landingpage](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Konfigurierbare Produkte werden beim Auschecken nicht mit der REST-API aktualisiert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein konfigurierbares Produkt mit Farb- und Größenattributen.
1. Wählen Sie **[!UICONTROL Options]** aus und fügen Sie das Produkt zum Warenkorb hinzu.
1. Gehen Sie zu **[!UICONTROL Checkout]**, aktualisieren Sie die Größe mehrmals mit Ausnahme der Menge und überprüfen Sie die Anfrage und die Antwort.
1. Wenn Sie die Größe aktualisieren, erhalten Sie die folgende Antwort.

```REST API
{"extension_attributes":{"configurable_item_options":[
{"option_id":"960","option_value":25083},
{"option_id":"801","option_value":177}
]}}
```

<u>Erwartete Ergebnisse</u>:

Der Wert wird gemäß den Änderungen aktualisiert.

<u>Tatsächliche Ergebnisse</u>:

`option_value` wird nicht aktualisiert. Wenn die Bestellung also aufgegeben wird, hat sie den alten Größenwert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tools] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im Handbuch Quality Patches Tool.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie in unserer Support [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html?lang=de)Wissensdatenbank, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist.

Weitere Informationen zu anderen in [!DNL QPT] verfügbaren Patches finden Sie unter [Patches verfügbar in [!DNL QPT]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im Handbuch zum Quality Patches Tool .
