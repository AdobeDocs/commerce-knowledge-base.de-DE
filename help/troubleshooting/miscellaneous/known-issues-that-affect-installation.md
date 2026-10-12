---
title: Bekannte Probleme, die die xdebug-Installation betreffen
description: Dieser Artikel bietet eine Lösung für den Fall, dass ein Ausnahmefehler auftritt, wenn Sie die optionale PHP-Erweiterung „xdebug“ verwenden.
exl-id: 5090ea99-e0c3-436a-809b-109701740927
feature: Install
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 0%
---
# Bekannte Probleme, die die xdebug-Installation betreffen

Dieser Artikel bietet eine Lösung für den Fall, dass ein Ausnahmefehler auftritt, wenn Sie die optionale PHP-`xdebug` verwenden.

* Während der Installation
* Zugriff auf Commerce Admin oder die Storefront nach erfolgreicher Installation

Beispielausnahme:

```php
Fatal error: Maximum function nesting level of '100' reached, aborting!
```

Um dieses Problem zu beheben, haben Sie folgende Möglichkeiten:

* Deaktivieren Sie die `xdebug`.
* Legen Sie den Wert von `xdebug.max_nesting_level` auf einen Wert von 200 oder höher fest. Weitere Informationen finden Sie unter [xdebug-Dokumentation](http://xdebug.org/docs/basic#max_nesting_level).

Nachdem Sie die Konfiguration von geändert oder `xdebug` deaktiviert haben, starten Sie Apache neu:

* CentOS: `sudo service httpd restart`
* Ubuntu: `sudo service apache2 restart`
