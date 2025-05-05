---
title: Abwärtsinkompatible Änderungen für [!DNL GraphQL] &grave;placeOrder&grave; [!DNL API] in Adobe Commerce 2.4.6-p8
promoted: true
description: Dieser Artikel enthält einen Patch für das bekannte Cloud- und On-Premise-Problem der Adobe Commerce-Version 2.4.6-p8, bei dem „placeOrder [!DNL GraphQL API]  keine erwartete Fehlerantwort zurückgibt, wie in vorherigen Patch-Versionen von 2.4.6 zu sehen. Dies kann zu einem fehlerhaften Kauferlebnis führen, wenn Händler die PWA-Storefront oder eine andere  [!DNL GraphQL API]-basierte Storefront für ihre Stores verwenden.
feature: Checkout, REST, GraphQL
role: Developer
exl-id: eacfb785-89e1-4bb7-8b6d-f7073746c9fa
source-git-commit: a84c3d296deb49d419be78f454696177a974d923
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# Abwärtsinkompatible Änderungen für [!DNL GraphQL] `placeOrder` [!DNL API] in Adobe Commerce 2.4.6-p8

Dieser Artikel enthält einen Patch für das bekannte Cloud- und On-Premise-Problem der Adobe Commerce-Version 2.4.6-p8, bei dem der `placeOrder`-[!DNL GraphQL API] keine erwartete Fehlerantwort zurückgibt, wie in vorherigen Patch-Versionen von 2.4.6 zu sehen. Dies kann zu einem fehlerhaften Checkout-Erlebnis für Händler führen, die [!DNL PWA] Storefront oder eine andere [!DNL GraphQL API] Storefront für ihre Stores verwenden.

>[!NOTE]
>
>Wenden Sie sich an den Support-Service, wenn beim Anwenden des Patches Probleme auftreten.

## Betroffene Produkte und Versionen

* Adobe Commerce in Cloud 2.4.6-p8
* Adobe Commerce On-Premises 2.4.6-p8

## Problem

Nach dem Upgrade auf Adobe Commerce 2.4.6-p8 Nur-Sicherheits-Patch gibt der [`placeOrder` [!DNL GraphQL API]](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/place-order/) keine erwartete Fehlerantwort zurück, wie in allen vorherigen Patch-Versionen von 2.4.6 zu sehen ist. Dies kann zu einem fehlerhaften Checkout-Erlebnis für Händler führen, die [!DNL PWA] Storefront oder eine andere [!DNL GraphQL API] Storefront für ihre Stores verwenden.

<u>Schritt zur Reproduktion</u>:

Führen Sie die `placeOrder` [!DNL GraphQL]-Anfrage aus, wenn Sie eine Fehlerantwort erwarten.

<u>Erwartetes Ergebnis</u>:

Sie erhalten eine erwartete Fehlerantwort.

<u>Tatsächliches </u>:

Anstelle einer erwarteten Fehlerantwort erhalten Sie eine erfolgreiche Antwort, jedoch mit einem neuen `errors`, der wie folgt aussieht:

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

## Lösung für Adobe Commerce on Cloud und lokale Adobe Commerce-Software

Um das Problem zu beheben, wenden Sie den Patch an.
Um ihn herunterzuladen, klicken Sie auf den folgenden Link:

[ac-13283-composer-patch.zip](assets/ac-13283-composer-patch.zip)

## Anbringen des Pflasters

Entpacken Sie die Datei und [ Sie in unserer Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html)Wissensdatenbank die Anleitung „So wenden Sie einen Composer-Patch von Adobe an“.

## Nur für Adobe Commerce on Cloud-Händler - Ermitteln, ob Patches angewendet wurden

Da es nicht einfach möglich ist, zu überprüfen, ob das Problem behoben wurde, sollten Sie überprüfen, ob der Patch erfolgreich angewendet wurde.

<u>Sie können dazu die folgenden Schritte ausführen, indem Sie die Beispieldatei `VULN-27015-2.4.7_COMPOSER.patch`als Beispiel **verwenden</u>**:

1. [Installieren Sie  [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Führen Sie den folgenden Befehl aus:<br>
   ![ac-13283-tell-if-patch-applied-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. Es sollte eine ähnliche Ausgabe angezeigt werden, bei der VULN-27015 den Status *Angewendet* zurückgibt:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->
