---
title: Während der Installation tritt bei Reflection Exception ein Fehler auf
description: Dieser Artikel bietet eine Lösung für den Reflection Exception-Fehler während der Installation.
exl-id: aed5f297-1339-4171-9392-04b3f93277ee
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '96'
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

Geben Sie als [Eigentümer des Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/file-system/overview)Dateisystems oder als Benutzer mit `root` die folgenden Befehle ein:

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
