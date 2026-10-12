---
title: Während der Installation tritt bei Reflection Exception ein Fehler auf
description: Dieser Artikel bietet eine Lösung für den Reflection Exception-Fehler während der Installation.
exl-id: aed5f297-1339-4171-9392-04b3f93277ee
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
source-wordcount: '107'
ht-degree: 0%
---
# Während der Installation tritt bei Reflection Exception ein Fehler auf

Dieser Artikel bietet eine Lösung für den Reflection Exception-Fehler während der Installation.

## Details {#details}

Während der Installation wird eine Meldung ähnlich der folgenden angezeigt:

```php
[ERROR] exception 'ReflectionException' with message 'Class Magento\Framework\StoreManagerInterface does not exist' in /<path>/lib/internal/Magento/Framework/Code/Reader/ClassReader.php
```

## Lösung {#solution}

Löschen Sie alle Ordner und Dateien im `var`-Unterverzeichnis von Adobe Commerce und installieren Sie die Adobe Commerce-Software erneut.

Geben Sie als [Eigentümer des Adobe Commerce](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/prerequisites/file-system/overview)Dateisystems oder als Benutzer mit `root` die folgenden Befehle ein:

```bash
$ cd <your Magento install directory>/var
```

```bash
$ rm -rf var/cache/* di/* generation/* page_cache/*
```

### Redis {#redis}

Wenn Sie Redis verwenden und dennoch einen Fehler erhalten, löschen Sie den Redis-Cache wie folgt:

```bash
$ redis-cli FLUSHALL
```
