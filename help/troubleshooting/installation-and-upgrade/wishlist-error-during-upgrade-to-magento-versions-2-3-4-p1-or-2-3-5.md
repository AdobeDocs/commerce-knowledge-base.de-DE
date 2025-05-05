---
title: Wunschlistenfehler beim Upgrade auf die Adobe Commerce-Versionen 2.3.4-p1 oder 2.3.5
description: Dieser Artikel enthält eine Fehlerbehebung für das bekannte Problem beim Upgrade auf Adobe Commerce 2.3.4-p1 und 2.3.5 im Zusammenhang mit einem Wishlist-Fehler beim Upgrade auf diese Versionen.
exl-id: 97479615-bf3f-4544-a9c1-8f19ba74318e
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# Wunschlistenfehler beim Upgrade auf die Adobe Commerce-Versionen 2.3.4-p1 oder 2.3.5

Dieser Artikel enthält eine Fehlerbehebung für das bekannte Problem beim Upgrade auf Adobe Commerce 2.3.4-p1 und 2.3.5 im Zusammenhang mit einem Wishlist-Fehler beim Upgrade auf diese Versionen.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.3.4-p1 und 2.3.5
* Adobe Commerce On-Premises 2.3.4-p1 und 2.3.5

## Problem

Beim Upgrade Ihres Adobe Commerce (alle Bereitstellungsmethoden) und Ihrer Magento Open Source auf Version 2.3.5 oder 2.3.4-p1 wird Ihnen möglicherweise eine Fehlermeldung auf der Wunschliste (siehe unten) angezeigt:

```php
Magento_Wishlist
```

Fehlerkorrektur - Der Fehler wird durch ein Upgrade von Adobe Commerce (alle Bereitstellungsmethoden)/Magneto Open Source Version 2.3.4-p1 **auf Version 2.3.4-p2** oder von Adobe Commerce (alle Bereitstellungsmethoden)/Magneto Open Source Version 2.3.5 **auf Version 2.3.5-p1**.

<u>Schritte zur Reproduktion</u>:

Aktualisieren Sie Ihre Adobe Commerce (alle Bereitstellungsmethoden)/Magento Open Source auf Version 2.3.4-p1 oder 2.3.5.

<u>Erwartetes Ergebnis</u>:

Das Upgrade auf Adobe Commerce (alle Bereitstellungsmethoden)/Magento Open Source 2.3.4-p1 oder 2.3.5 wird normal abgeschlossen.

<u>Tatsächliches </u>:

Während des Upgrades erhalten Sie diese Fehlermeldung:

```php
Module ‘Magento_Wishlist’:

Unable to apply data patch Magento\Wishlist\Setup\Patch\Data\CleanUpData for module Magento_Wishlist. Original exception message: Unable to unserialize value. Error: Syntax error
```

## Lösungen

* Wenn Sie ein Upgrade auf Adobe Commerce (alle Bereitstellungsmethoden)/Magneto Open Source Version 2.3.5 durchgeführt haben, **aktualisieren Sie auf Version 2.3.5-p1**. Adobe Commerce (alle Bereitstellungsmethoden)/Magento Open Source Version 2.3.5-p1 ersetzt 2.3.5.
* Wenn Sie ein Upgrade auf Adobe Commerce (alle Bereitstellungsmethoden)/Magento Open Source 2.3.4-p1 durchgeführt haben, **aktualisieren Sie auf Version 2.3.4-p2**. Adobe Commerce (alle Bereitstellungsmethoden)/Magneto Open Source Version 2.3.4-p2 ersetzt Version 2.3.4-p1.

## Verwandtes Lesen

In unserer Entwicklerdokumentation:

* [Handbuch zu Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/overview)
* [Adobe Commerce auf Cloud-Infrastruktur - Adobe Commerce-Version aktualisieren](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version)
* [Adobe Commerce On-Premise und Magento Open Source - Aktualisieren Sie die Adobe Commerce-Anwendung und -Module](https://experienceleague.adobe.com/de/docs/commerce-operations/upgrade-guide/overview)
* [Wunschlistenelement Seite konfigurieren](https://developer.adobe.com/commerce/frontend-core/guide/layouts/product-layouts/#wishlist-item-configure-page)
* [Module für erweiterte Berichterstellung](https://developer.adobe.com/commerce/php/development/advanced-reporting/modules/)
