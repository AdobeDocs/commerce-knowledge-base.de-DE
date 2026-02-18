---
title: Fehlerbehebung beim [!UICONTROL Product Recommendations] in Adobe Commerce
description: In diesem Artikel werden Vorschläge zur Fehlerbehebung für das [!UICONTROL Product Recommendations] in Adobe Commerce behandelt.
exl-id: 431ee31e-eb5b-400c-9c99-cc86613453d7
feature: Cache, Compliance, Extensions, Marketing Tools, Personalization, Products, Recommendations
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Fehlerbehebung beim [!UICONTROL Product Recommendations] in Adobe Commerce

In diesem Artikel werden Vorschläge zur Fehlerbehebung bei Folgendem beschrieben

```php
magento/product-recommendations
```

Modul und seine Abhängigkeit

```php
saas-export
```

-Modul verwenden, da beide Module ausgeführt werden müssen, damit das [!UICONTROL Product Recommendations]-Tool in Adobe Commerce verwendet werden kann.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.4.4 - 2.4.7

## Fehlerbehebung beim Modul für Produktempfehlungen

Wenn Sie Folgendes konfiguriert haben

```php
magento/product-recommendations
```

Modul richtig, ([[!UICONTROL Product Recommendations - Install and Configure]](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure) Sie in unserer Entwicklerdokumentation nach.), aber Sie sehen keine Empfehlungen, versuchen Sie Folgendes:

* Möglicherweise hatte das Modul nicht genügend Zeit, um Verhaltensdaten zu erfassen. Lassen Sie das System 24 Stunden laufen, damit es mit der Datenerfassung beginnen kann. Ziehen Sie die Bereitstellung eines Empfehlungstyps in Betracht, für den keine Verhaltensdaten erforderlich sind, z. B. &quot;*Ähnliche Themen*.

* Wenn Sie die von Ihnen konfigurierten Empfehlungen nicht sehen, gibt es möglicherweise noch nicht genügend Daten, um Empfehlungen für die Benutzenden zu erstellen.

* Stellen Sie sicher, dass der [!DNL SaaS] oder der [!DNL API] gültig sind. Wenn bei der Initialisierung der Produktempfehlungen nach Angabe Ihres [!DNL SaaS]-Datenbereichs oder Ihres [!DNL API]-Schlüssels ein Fehler auftritt, stellen Sie sicher, dass Sie [[!DNL SaaS] Datenbereich und  [!DNL API] -Schlüssel](https://experienceleague.adobe.com/en/docs/commerce-admin/config/services/saas) (in unserem Benutzerhandbuch) korrekt eingegeben haben. Um sicherzustellen, dass [!DNL MageID] und [!DNL API] verknüpft sind, muss der Benutzer, dem die [!DNL MageID] gehört, in der Regel der Benutzer sein, der die Adobe Commerce-Lizenz besitzt, auch der Benutzer sein, der den [!DNL API] generiert. Wenn Sie die verwendete [!DNL MageID] ändern müssen, [ Sie ein Support-Ticket ](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket).

>[!NOTE]
>
>Wenn [**[!UICONTROL Cookie Restriction Mode]**](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law) (in unserem Benutzerhandbuch) *aktiviert* erfasst Adobe Commerce keine Verhaltensdaten, bis der Käufer einwilligt. Wenn **[!UICONTROL Cookie Restriction Mode]***deaktiviert* ist, erfasst Adobe Commerce standardmäßig Verhaltensdaten.

## Modul [!DNL SaaS] Katalogausgabe

Bei Problemen mit dem [!DNL SaaS]-Export (

```php
saas-export
```

)-Modul:

1. Bestätigen Sie, dass die [[!DNL cron]](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) (in unserer Entwicklerdokumentation) ausgeführt werden.
1. Bestätigen Sie, dass die [[!UICONTROL indexers]](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers) (in unserer Entwicklerdokumentation) ausgeführt werden und die    ```php    Product Feed    ```    [!UICONTROL indexer] ist festgelegt auf    ```php    Update by Schedule    ```    .
1. Bestätigen Sie, dass die Module *aktiviert* sind. Die    ```php    saas-export    ```    Metapaket installiert die folgenden Module, die alle *aktiviert* sein müssen:    ```php    "magento/module-catalog-data-exporter"      "magento/module-catalog-inventory-data-exporter"      "magento/module-catalog-url-rewrite-data-exporter"      "magento/module-configurable-product-data-exporter"      "magento/module-data-exporter"      "magento/module-saas-catalog"    ```
1. Überprüfen Sie die [Protokolle](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/enable-logging) (in unserer Entwicklerdokumentation). Stellen Sie sicher, dass die oben genannten Module keine Fehler enthalten.
1. Aktualisieren Sie die [!UICONTROL Configuration cache]. Wechseln Sie **System** > **Tools** > **Cache-Verwaltung** und löschen Sie die [!UICONTROL Configuration cache].
1. Bestätigen Sie, dass die `cde_products_products_feed` Datenbanktabelle Daten enthält.

   >[!NOTE]
   >
   >Wenn Sie diese Tabelle nicht finden können, überprüfen Sie die `catalog_data_exporter_products`. Der Tabellenname wurde in der [!DNL Data Export] Version 103.3.0 geändert.

## Ereignisse

[Verify Event Collection](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/verify) beschreibt in unserer Entwicklerdokumentation die Verhaltensereignisse, die an Adobe Commerce gesendet werden.

## Verwandtes Lesen

* [Product Recommendations-Administrator-Entwicklung](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/developer/development-overview) in unserer Entwicklerdokumentation
* [Einführung in Produktempfehlungen](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/overview) im Produktempfehlungshandbuch
* [Erstellen von Produktempfehlungen](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/admin/create) im Produktempfehlungshandbuch
* [Überprüfen Sie die Protokolle und ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/troubleshooting-logging) Sie Fehler“ im Handbuch [!DNL SaaS] Datenexport .
* [[!DNL SaaS] Versionshinweise zur Datenexporterweiterung](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes) im Adobe Commerce-Datenexporthandbuch für [!DNL SaaS] Services
* [Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook

