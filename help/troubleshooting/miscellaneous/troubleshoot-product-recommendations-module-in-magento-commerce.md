---
title: Fehlerbehebung für das [!UICONTROL Product Recommendations]-Modul in Adobe Commerce
description: In diesem Artikel werden Vorschläge zur Fehlerbehebung für das [!UICONTROL Product Recommendations]-Modul in Adobe Commerce vorgestellt.
exl-id: 431ee31e-eb5b-400c-9c99-cc86613453d7
feature: Cache, Compliance, Extensions, Marketing Tools, Personalization, Products, Recommendations
role: Developer
source-git-commit: af9ee28c5819a9d1b97411210816bfe8a9522614
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# Fehlerbehebung für das [!UICONTROL Product Recommendations]-Modul in Adobe Commerce

In diesem Artikel werden Vorschläge zur Fehlerbehebung für

```php
magento/product-recommendations
```

-Modul und seine Abhängigkeit

```php
saas-export
```

-Modul, da Sie beide Module benötigen, um das Tool [!UICONTROL Product Recommendations] in Adobe Commerce verwenden zu können.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.4.4 - 2.4.7

## Fehlerbehebung für das Modul &quot;Produktempfehlungen&quot;

Wenn Sie die

```php
magento/product-recommendations
```

korrekt hinzugefügt werden (Überprüfen Sie in unserer Entwicklerdokumentation [[!UICONTROL Product Recommendations - Install and Configure]](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure).) Sie sehen jedoch keine Empfehlungen, versuchen Sie Folgendes:

* Es ist möglich, dass das Modul nicht genügend Zeit hatte, Verhaltensdaten zu erfassen. Lassen Sie das System 24 Stunden laufen, damit es mit der Datenerfassung beginnen kann. Erwägen Sie die Bereitstellung eines Empfehlungstyps, für den keine Verhaltensdaten erforderlich sind, z. B. &quot;*Mehr wie dieser*&quot;.

* Wenn die von Ihnen konfigurierten Empfehlungen nicht angezeigt werden, sind möglicherweise noch nicht genügend Daten vorhanden, um Empfehlungen für den Benutzer zu erstellen.

* Stellen Sie sicher, dass der [!DNL SaaS] Datenraum oder der [!DNL API] Schlüssel gültig sind. Wenn bei der Initialisierung der Produktempfehlungen ein Fehler auftritt, nachdem Sie Ihren [!DNL SaaS] Datenraum oder Ihren [!DNL API] -Schlüssel angegeben haben, überprüfen Sie, ob Sie den [[!DNL SaaS] Datenraum und den  [!DNL API] Schlüssel](https://experienceleague.adobe.com/en/docs/commerce-admin/config/services/saas) (in unserem Benutzerhandbuch) richtig eingegeben haben. Um sicherzustellen, dass die Schlüssel [!DNL MageID] und [!DNL API] verknüpft sind, muss der Benutzer, der Inhaber der [!DNL MageID] ist (normalerweise der Benutzer, der Inhaber der Adobe Commerce-Lizenz ist) derselbe Benutzer sein, der den Schlüssel [!DNL API] generiert. Wenn Sie die verwendete [!DNL MageID] ändern müssen, senden Sie ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).[

>[!NOTE]
>
>Wenn [**[!UICONTROL Cookie Restriction Mode]**](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law) (in unserem Benutzerhandbuch) *enabled* ist, erfasst Adobe Commerce erst Verhaltensdaten, wenn der Käufer zustimmt. Wenn **[!UICONTROL Cookie Restriction Mode]***disabled* ist, erfasst Adobe Commerce standardmäßig Verhaltensdaten.

## Exportmodul Catalog [!DNL SaaS]

Bei Problemen im Zusammenhang mit dem Katalog [!DNL SaaS] Export (

```php
saas-export
```

)-Modul:

1. Vergewissern Sie sich, dass die Aufträge für [[!DNL cron]](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) (in unserer Entwicklerdokumentation) ausgeführt werden.
1. Vergewissern Sie sich, dass der [[!UICONTROL indexers]](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers) (in unserer Entwicklerdokumentation) ausgeführt wird und die    ```php    Product Feed    ```    [!UICONTROL indexer] ist auf    ```php    Update by Schedule    ```    .
1. Vergewissern Sie sich, dass die Module *aktiviert* sind. Die    ```php    saas-export    ```    metapackage installiert die folgenden Module, die alle *enabled* sein müssen:    ```php    "magento/module-catalog-data-exporter"      "magento/module-catalog-inventory-data-exporter"      "magento/module-catalog-url-rewrite-data-exporter"      "magento/module-configurable-product-data-exporter"      "magento/module-data-exporter"      "magento/module-saas-catalog"    ```
1. Überprüfen Sie die [logs](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/enable-logging) (in unserer Entwicklerdokumentation). Stellen Sie sicher, dass mit den oben genannten Modulen keine Fehler verbunden sind.
1. Aktualisieren Sie die [!UICONTROL Configuration cache]. Wechseln Sie zu &quot;**System**&quot;> &quot;**Tools**&quot;> &quot;**Cache-Verwaltung**&quot;und löschen Sie &quot;[!UICONTROL Configuration cache]&quot;.
1. Vergewissern Sie sich, dass die Datenbanktabelle `cde_products_products_feed` Daten enthält.

   >[!NOTE]
   >
   >Wenn Sie diese Tabelle nicht finden, überprüfen Sie die Tabelle `catalog_data_exporter_products` . Der Tabellenname wurde in Version 103.3.0 von [!DNL Data Export] geändert.

## Veranstaltungen

[Verify Event Collection](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/verify) in unserer Entwicklerdokumentation beschreibt die Verhaltensereignisse, die an Adobe Commerce gesendet werden.

## Verwandtes Lesen

* [Entwicklung für Produkt-Recommendations-Administratoren](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/developer/development-overview) in unserer Entwicklerdokumentation
* [Einführung in die Produkt-Recommendations](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/overview) im Produkt-Recommendations-Handbuch
* [Erstellen Sie Produkt-Recommendations](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/admin/create) im Handbuch für Produkt-Recommendations
* [Überprüfen Sie die Protokolle und führen Sie eine Fehlerbehebung für ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/troubleshooting-logging) im [!DNL SaaS] Data Export Guide durch.
* [[!DNL SaaS] Versionshinweise zur Datenexport-Erweiterung](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes) im Adobe Commerce-Datenexportleitfaden für [!DNL SaaS] -Dienste
