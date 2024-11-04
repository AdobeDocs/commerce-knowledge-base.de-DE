---
title: "Abwärtsinkompatible Änderungen für [!DNL GraphQL] `placeOrder` [!DNL API] in Adobe Commerce 2.4.6-p8"
promoted: true
description: Dieser Artikel enthält einen Patch für die bekannte Adobe Commerce-Version 2.4.6-p8 Cloud und das On-Premise-Problem, bei dem "placeOrder" [!DNL GraphQL API] keine erwartete Fehlerantwort zurückgibt, wie in früheren Patch-Versionen 2.4.6 gezeigt. Dies kann dazu führen, dass Kaufleute, die eine PWA-Storefront oder eine andere [!DNL GraphQL API]-basierte Storefront für ihre Geschäfte verwenden, nicht mehr auschecken können.
feature: Checkout, REST, GraphQL
role: Developer
source-git-commit: 01b79c75df34de20f1ff50ab40c0a8d608ffa779
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# Abwärtskompatible Änderungen für [!DNL GraphQL] `placeOrder` [!DNL API] in Adobe Commerce 2.4.6-p8

Dieser Artikel enthält einen Patch für die bekannte Adobe Commerce-Version 2.4.6-p8 Cloud und das On-Premise-Problem, bei dem die `placeOrder` [!DNL GraphQL API] keine erwartete Fehlerantwort zurückgibt, wie in früheren Patch-Versionen 2.4.6 gezeigt. Dies kann dazu führen, dass Kaufleute, die eine [!DNL PWA] Storefront oder eine andere [!DNL GraphQL API]-basierte Storefront für ihre Geschäfte verwenden, nicht mehr auschecken können.

>[!NOTE]
>
>Wenden Sie sich an den Support Services , wenn Probleme beim Anwenden des Patches auftreten.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud 2.4.6-p8
* Adobe Commerce vor Ort 2.4.6-p8

## Problem

Nach dem Upgrade auf den Sicherheits-Patch für Adobe Commerce 2.4.6-p8 gibt der Patch [`placeOrder` [!DNL GraphQL API]](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/place-order/) keine erwartete Fehlerantwort zurück, wie in früheren Patch-Versionen 2.4.6 zu sehen war. Dies kann dazu führen, dass Kaufleute, die eine [!DNL PWA] Storefront oder eine andere [!DNL GraphQL API]-basierte Storefront für ihre Geschäfte verwenden, nicht mehr auschecken können.

<u>Schritt zum Reproduzieren</u>:

Führen Sie die `placeOrder` [!DNL GraphQL] -Anfrage aus, bei der Sie eine Fehlerantwort erwarten.

<u>Erwartetes Ergebnis</u>:

Sie erhalten eine erwartete Fehlerantwort.

<u>Tatsächliches Ergebnis</u>:

Anstelle einer erwarteten Fehlerantwort erhalten Sie eine erfolgreiche Antwort, jedoch mit einem neuen `errors` -Schlüssel, der wie folgt aussieht:

```
{
    "data": {
        "placeOrder": {
            "order": null,
            "__typename": "PlaceOrderOutput"
        }
    }
}
```

## Lösung für Adobe Commerce auf Cloud- und Adobe Commerce-On-Premise-Software

Um das Problem zu lösen, wenden Sie den Patch an.
Um es herunterzuladen, klicken Sie auf den folgenden Link:

[ac-13283-composer-patch.zip](assets/ac-13283-composer-patch.zip)

## Anwenden des Pflasters

Entpacken Sie die Datei und finden Sie Anweisungen unter [Anwenden eines von Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) bereitgestellten Composer-Patches in unserer Support-Wissensdatenbank.

## Nur für Adobe Commerce für Cloud-Händler - Ermitteln, ob Patches angewendet wurden

Da es nicht einfach zu überprüfen ist, ob das Problem gepatcht wurde, sollten Sie überprüfen, ob der Patch erfolgreich angewendet wurde.

<u>Gehen Sie dazu wie folgt vor, indem Sie die Beispieldatei `VULN-27015-2.4.7_COMPOSER.patch` **als Beispiel</u>** verwenden:

1. [Installieren Sie den  [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Führen Sie den Befehl aus:<br>
   ![ac-13283-tell-if-patch-apply-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. Sie sollten die Ausgabe ähnlich der folgenden sehen, bei der VULN-27015 den Status *Angewandt* zurückgibt:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->

