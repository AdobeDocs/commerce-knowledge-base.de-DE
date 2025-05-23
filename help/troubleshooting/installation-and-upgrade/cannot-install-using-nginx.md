---
title: Installation mit nginx nicht möglich
description: Dieser Artikel enthält eine Fehlerbehebung für eine fehlgeschlagene Adobe Commerce-Installation bei Verwendung des nginx-Webservers.
exl-id: 0af90c7e-0733-41c8-b217-9595b133fa95
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '87'
ht-degree: 0%

---

# Installation mit nginx nicht möglich

Dieser Artikel enthält eine Fehlerbehebung für eine fehlgeschlagene Adobe Commerce-Installation bei Verwendung des nginx-Webservers.

## Problem

Wenn Sie den nginx-Webserver verwenden und versuchen, die Adobe Commerce-Software zu installieren, schlägt die Installation manchmal fehl.

## Lösung

Sie können das Problem durch den folgenden Fehler im `var/report`-Verzeichnis bestätigen:

```php
NOTE: You cannot install Adobe Commerce using the Setup Wizard because the Adobe Commerce setup directory cannot be accessed.
You can install Adobe Commerce using either the command line or you must restore access to the following directory: /var/www/html/setup
If you are using the sample nginx configuration, please go to http://ce.mtf03.bcn.magento.com/setup/";i:1;s:641:"#0 /var/www/html/lib/internal/Magento/Framework/App/Http.php(213): Magento\Framework\App\Http->redirectToSetup(Object(Magento\Framework\App\Bootstrap), Object(Exception))
```

### Abhilfe

Installieren Sie die Adobe Commerce-Software über [Befehlszeile](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/advanced).
