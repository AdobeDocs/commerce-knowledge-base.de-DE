---
title: Wunschlistenfehler beim Upgrade auf die Adobe Commerce-Versionen 2.3.4-p1 oder 2.3.5
description: Dieser Artikel enthält eine Fehlerbehebung für das bekannte Problem beim Upgrade auf Adobe Commerce 2.3.4-p1 und 2.3.5 im Zusammenhang mit einem Wishlist-Fehler beim Upgrade auf diese Versionen.
exl-id: 97479615-bf3f-4544-a9c1-8f19ba74318e
feature: Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%
---
# Wunschlistenfehler beim Upgrade auf die Adobe Commerce-Versionen 2.3.4-p1 oder 2.3.5

Dieser Artikel enthält eine Fehlerbehebung für das bekannte Problem beim Upgrade auf Adobe Commerce 2.3.4-p1 und 2.3.5 im Zusammenhang mit einem Wishlist-Fehler beim Upgrade auf diese Versionen.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.3.4-p1 und 2.3.5
* Adobe Commerce On-Premises 2.3.4-p1 und 2.3.5

## Problem

Beim Upgrade von Adobe Commerce (alle Bereitstellungsmethoden) und Magento Open Source auf Version 2.3.5 oder 2.3.4-p1 wird möglicherweise ein Wunschlistenfehler (siehe unten) aus dem Modul angezeigt:

```php
Magento_Wishlist
```

Fehlerkorrektur - Der Fehler wird durch ein Upgrade von Adobe Commerce (alle Bereitstellungsmethoden)/Magneto Open Source Version 2.3.4-p1 **auf Version 2.3.4-p2** oder von Adobe Commerce (alle Bereitstellungsmethoden)/Magneto Open Source Version 2.3.5 **auf Version 2.3.5-p1**.

<u>Schritte zur Reproduktion</u>:

Aktualisieren Sie Adobe Commerce (alle Bereitstellungsmethoden)/Magento Open Source auf Version 2.3.4-p1 oder 2.3.5.

<u>Erwartetes Ergebnis</u>:

Das Upgrade auf Adobe Commerce (alle Bereitstellungsmethoden)/Magento Open Source Version 2.3.4-p1 oder 2.3.5 wird normal abgeschlossen.

<u>Tatsächliches </u>:

Während des Upgrades erhalten Sie diese Fehlermeldung:

```php
Module ‘Magento_Wishlist’:

Unable to apply data patch Magento\Wishlist\Setup\Patch\Data\CleanUpData for module Magento_Wishlist. Original exception message: Unable to unserialize value. Error: Syntax error
```

## Lösungen

* Wenn Sie ein Upgrade auf Adobe Commerce (alle Bereitstellungsmethoden)/Magneto Open Source Version 2.3.5 durchgeführt haben, **aktualisieren Sie auf Version 2.3.5-p1**. Adobe Commerce (alle Bereitstellungsmethoden)/Magento Open Source Version 2.3.5-p1 ersetzt 2.3.5.
* Wenn Sie ein Upgrade auf Adobe Commerce (alle Bereitstellungsmethoden)/Magento Open Source Version 2.3.4-p1 durchgeführt haben, **aktualisieren Sie auf Version 2.3.4-p2**. Adobe Commerce (alle Bereitstellungsmethoden)/Magneto Open Source Version 2.3.4-p2 ersetzt Version 2.3.4-p1.

## Verwandtes Lesen

In unserer Entwicklerdokumentation:

* [Handbuch zu Adobe Commerce in Cloud-Infrastrukturen](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/overview)
* [Adobe Commerce auf Cloud-Infrastruktur - Adobe Commerce-Version aktualisieren](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version)
* [Adobe Commerce On-Premise und Magento Open Source - Aktualisieren der Adobe Commerce-Anwendung und -Module](https://experienceleague.adobe.com/de/docs/commerce-operations/upgrade-guide/overview)
* [Wunschlistenelement Seite konfigurieren](https://developer.adobe.com/commerce/frontend-core/guide/layouts/product-layouts#wishlist-item-configure-page)
* [Module mit erweitertem Reporting](https://developer.adobe.com/commerce/php/development/advanced-reporting/modules/)
