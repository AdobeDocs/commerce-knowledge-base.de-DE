---
title: Wishlist-Fehler während der Aktualisierung auf Adobe Commerce-Versionen 2.3.4-p1 oder 2.3.5
description: Dieser Artikel enthält eine Fehlerbehebung für das bekannte Problem bei der Aktualisierung auf die Adobe Commerce-Versionen 2.3.4-p1 und 2.3.5 im Zusammenhang mit einem Wunschlistenfehler während der Aktualisierung auf diese Versionen.
exl-id: 97479615-bf3f-4544-a9c1-8f19ba74318e
feature: Install, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# Wishlist-Fehler während der Aktualisierung auf Adobe Commerce-Versionen 2.3.4-p1 oder 2.3.5

Dieser Artikel enthält eine Fehlerbehebung für das bekannte Problem bei der Aktualisierung auf die Adobe Commerce-Versionen 2.3.4-p1 und 2.3.5 im Zusammenhang mit einem Wunschlistenfehler während der Aktualisierung auf diese Versionen.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.3.4-p1 und 2.3.5
* Adobe Commerce vor Ort 2.3.4-p1 und 2.3.5

## Problem

Beim Aktualisieren Ihrer Adobe Commerce (alle Bereitstellungsmethoden) und der Magento Open Source auf Version 2.3.5 oder 2.3.4-p1 könnten Sie einen Wunschlistenfehler (siehe unten) vom Modul erhalten:

```php
Magento_Wishlist
```

Upgrade von Adobe Commerce (alle Bereitstellungsmethoden)/Magneto Open Source Version 2.3.4-p1 **auf Version 2.3.4-p2** oder von Adobe Commerce (alle Bereitstellungsmethoden)/Magneto Open Source Version 2.3.5 **zu Version 2.3.5-p1** löst den Fehler.

<u>Zu reproduzierende Schritte</u>:

Aktualisieren Sie Ihre Adobe Commerce (alle Bereitstellungsmethoden)/Magento Open Source auf Version 2.3.4-p1 oder 2.3.5.

<u>Erwartetes Ergebnis</u>:

Der Upgrade-Prozess auf Adobe Commerce (alle Bereitstellungsmethoden)/Magento Open Source-Version 2.3.4-p1 oder 2.3.5 wird normal ausgeführt.

<u>Tatsächliches Ergebnis</u>:

Während des Upgrades erhalten Sie diesen Fehler:

```php
Module ‘Magento_Wishlist’:

Unable to apply data patch Magento\Wishlist\Setup\Patch\Data\CleanUpData for module Magento_Wishlist. Original exception message: Unable to unserialize value. Error: Syntax error
```

## Lösungen

* Wenn Sie auf Adobe Commerce (alle Bereitstellungsmethoden)/Magneto Open Source Version 2.3.5 aktualisieren, **Upgrade auf Version 2.3.5-p1**. Adobe Commerce (alle Bereitstellungsmethoden)/Magento Open Source-Version 2.3.5-p1 ersetzt 2.3.5.
* Wenn Sie auf Adobe Commerce (alle Bereitstellungsmethoden)/Magento Open Source-Version 2.3.4-p1 aktualisieren, **Upgrade auf Version 2.3.4-p2**. Adobe Commerce (alle Bereitstellungsmethoden)/Magneto Open Source Version 2.3.4-p2 ersetzt Version 2.3.4-p1.

## Verwandtes Lesen

In unserer Entwicklerdokumentation:

* [Handbuch zur Cloud-Infrastruktur für Adobe Commerce](https://devdocs.magento.com/cloud/bk-cloud.html)
* [Adobe Commerce in der Cloud-Infrastruktur - Upgrade der Adobe Commerce-Version](https://devdocs.magento.com/cloud/project/project-upgrade.html)
* [Adobe Commerce vor Ort und Magento Open Source - Aktualisierung der Adobe Commerce-Anwendung und -Module](https://devdocs.magento.com/guides/v2.3/comp-mgr/bk-compman-upgrade-guide.html)
* [Seite &quot;wishlist item configure&quot;](https://devdocs.magento.com/guides/v2.3/frontend-dev-guide/layouts/product-layouts.html#wishlist-item-configure-page)
* [Module für erweiterte Berichterstellung](https://devdocs.magento.com/guides/v2.3/advanced-reporting/modules.html)
