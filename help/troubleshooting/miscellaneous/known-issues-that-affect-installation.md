---
title: Bekannte Probleme, die sich auf die Installation von xdebug auswirken
description: Dieser Artikel bietet eine Lösung für Fälle, in denen ein Ausnahmefehler auftritt, wenn Sie die optionale PHP-Erweiterung "xdebug"verwenden.
exl-id: 5090ea99-e0c3-436a-809b-109701740927
feature: Install
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---

# Bekannte Probleme, die sich auf die Installation von xdebug auswirken

Dieser Artikel bietet eine Lösung für Fälle, in denen bei Verwendung der optionalen PHP-Erweiterung `xdebug` ein Ausnahmefehler auftritt.

* Während der Installation
* Zugriff auf Commerce Admin oder Storefront nach erfolgreicher Installation

Beispielausnahme:

```php
Fatal error: Maximum function nesting level of '100' reached, aborting!
```

Um dieses Problem zu beheben, können Sie:

* Deaktivieren Sie die Erweiterung `xdebug` .
* Setzen Sie den Wert von `xdebug.max_nesting_level` auf einen Wert größer/gleich 200. Weitere Informationen finden Sie in der [xdebug-Dokumentation](http://xdebug.org/docs/basic#max_nesting_level).

Nachdem Sie die Konfiguration von `xdebug` geändert oder deaktiviert haben, starten Sie Apache neu:

* CentOS: `sudo service httpd restart`
* Ubuntu: `sudo service apache2 restart`
