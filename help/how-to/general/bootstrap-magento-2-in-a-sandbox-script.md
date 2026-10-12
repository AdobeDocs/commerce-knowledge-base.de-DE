---
title: Bootstrap Adobe Commerce 2 in einem Sandbox-Skript
description: 'Um eine Adobe Commerce 2-Anwendung in einem Beispiel-Sandbox-Skript zu initialisieren, führen Sie das folgende Skript aus dem Adobe Commerce-Stammverzeichnis aus:'
exl-id: a6acb30a-5175-42c6-8de3-e80c9ae8dac1
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '60'
ht-degree: 0%
---
# Bootstrap Adobe Commerce 2 in einem Sandbox-Skript

Um eine Adobe Commerce 2-Anwendung in einem Beispiel-Sandbox-Skript zu initialisieren, führen Sie das folgende Skript aus dem Adobe Commerce-Stammverzeichnis aus:

```php
<?php

error_reporting(E_ALL | E_STRICT);
ini_set('display_errors', 1);

require __DIR__ . '/app/bootstrap.php';
$bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);
$objectManager = $bootstrap->getObjectManager();

//$model = $objectManager->get('Vendor\Module\Some\Model');
```
