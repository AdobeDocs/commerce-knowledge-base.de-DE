---
title: Während der Installation wird der Reflektions-Ausnahmefehler angezeigt
description: Dieser Artikel bietet eine Lösung für den Reflection Exception-Fehler während der Installation.
exl-id: aed5f297-1339-4171-9392-04b3f93277ee
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---

# Während der Installation wird der Reflektions-Ausnahmefehler angezeigt

Dieser Artikel bietet eine Lösung für den Reflection Exception-Fehler während der Installation.

## Details {#details}

Während der Installation wird eine Meldung ähnlich der folgenden angezeigt:

```php
[ERROR] exception 'ReflectionException' with message 'Class Magento\Framework\StoreManagerInterface does not exist' in /<path>/lib/internal/Magento/Framework/Code/Reader/ClassReader.php
```

## Lösung {#solution}

Löschen Sie alle Verzeichnisse und Dateien im Unterverzeichnis von Adobe Commerce `var` und installieren Sie die Adobe Commerce-Software erneut.

Geben Sie als Inhaber des Adobe Commerce-Dateisystems ](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-sys-perms-over.html) oder als Benutzer mit `root` -Berechtigungen die folgenden Befehle ein:[

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
