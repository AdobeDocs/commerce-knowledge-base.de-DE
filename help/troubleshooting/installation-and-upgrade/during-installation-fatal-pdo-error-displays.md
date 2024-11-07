---
title: Während der Installation wird ein schwerwiegender PDO-Fehler angezeigt
description: Dieser Artikel enthält eine Fehlerbehebung für einen Ausnahmefehler bei PDO während der Installation.
exl-id: d69908f0-71c9-48de-9369-6ada22f2b393
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 0%

---

# Während der Installation wird ein schwerwiegender PDO-Fehler angezeigt

Dieser Artikel enthält eine Fehlerbehebung für einen Ausnahmefehler bei PDO während der Installation.

## Problem

```php
PHP Fatal error:  Class 'PDO' not found in /var/www/html/magento2/setup/module/Magento/Setup/src/Module/Setup/ConnectionFactory.php on line 44
```

## Lösung

Stellen Sie sicher, dass Sie alle [erforderlichen PHP-Erweiterungen](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/php-settings) installieren.
