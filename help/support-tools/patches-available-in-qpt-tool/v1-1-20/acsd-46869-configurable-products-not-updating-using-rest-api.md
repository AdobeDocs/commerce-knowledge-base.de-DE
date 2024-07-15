---
title: "ACSD-46869: Konfigurierbare Produkte, die beim Checkout nicht mit der REST-API aktualisiert werden"
description: Der Patch ACSD-46869 behebt das Problem, dass die konfigurierbaren Produkte beim Checkout nicht mit der REST-API aktualisiert werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 installiert ist. Die Patch-ID ist ACSD-46869. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.
exl-id: d1bac489-f0f3-4b50-bc48-86c844230da7
feature: REST, Checkout, Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-46869: Konfigurierbare Produkte, die beim Checkout nicht mit der REST-API aktualisiert werden

Der Patch ACSD-46869 behebt das Problem, dass konfigurierbare Produkte beim Checkout nicht mit der REST-API aktualisiert werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 installiert ist. Die Patch-ID ist ACSD-46869. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der [[!DNL QPT] Landingpage](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Konfigurierbare Produkte werden beim Checkout nicht mit der REST-API aktualisiert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein konfigurierbares Produkt mit Attributen für Farbe und Größe.
1. Wählen Sie **[!UICONTROL Options]** aus und fügen Sie das Produkt zum Warenkorb hinzu.
1. Wechseln Sie zu &quot;**[!UICONTROL Checkout]**&quot;, aktualisieren Sie die Größe mehrmals mit Ausnahme von &quot;qty&quot;und überprüfen Sie die Anforderung und Antwort.
1. Sie erhalten die folgende Antwort, wenn Sie die Größe aktualisieren.

```REST API
{"extension_attributes":{"configurable_item_options":[
{"option_id":"960","option_value":25083},
{"option_id":"801","option_value":177}
]}}
```

<u>Erwartete Ergebnisse</u>:

Der Wert wird entsprechend den Änderungen aktualisiert.

<u>Tatsächliche Ergebnisse</u>:

`option_value` wird nicht aktualisiert. Wenn also die Bestellung platziert wird, hat sie den alten Größenwert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tools] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im Handbuch zum Werkzeug für Qualitätsmuster.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://devdocs.magento.com/cloud/project/project-patch.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitätspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in [!DNL QPT] verfügbaren Patches finden Sie unter [In  [!DNL QPT]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) verfügbare Patches im Handbuch zum Werkzeug für Qualitätsmuster .
