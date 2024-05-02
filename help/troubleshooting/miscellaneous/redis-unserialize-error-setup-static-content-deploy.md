---
title: Redis unserialize error `setup:static-content:deploy"
description: Dieser Artikel enthält eine Fehlerbehebung für den Fehler "Redis unserialize", wenn `magento setup ausgeführt wird.:static-content:bereitstellen".
exl-id: 4bc88933-3bf9-4742-b864-b82d3c1b07a9
feature: Cache, Deploy, Page Content, SCD, Services, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Deserialisierungs-Fehler zurücksetzen `setup:static-content:deploy`

Dieser Artikel enthält eine Fehlerbehebung für den Fehler Redis unserialize bei der Ausführung `magento setup:static-content:deploy`.

Läuft `magento setup:static-content:deploy` verursacht den Redis-Fehler:

```
[Exception]
Notice: unserialize(): Error at offset 0 of 1 bytes in
/var/www/domain.com/vendor/magento/module-config/App/Config/Type/System.php on line 214
```

Das Problem wird durch parallele Störprozesse in der Redis-Verbindung verursacht.

Führen Sie zum Auflösen `setup:static-content:deploy` in einem Einzelthread-Modus durch Festlegen der folgenden Umgebungsvariablen:

```
STATIC_CONTENT_THREADS =1
```

oder führen Sie die `setup:static-content:deploy` -Befehl, gefolgt von `-j 1` (oder `--jobs=1` ).

Beachten Sie, dass das Deaktivieren der Multithreading-Funktion die Bereitstellung statischer Assets verlangsamt.

## Betroffene Versionen

* Adobe Commerce vor Ort: 2.1.2 und höher
* Adobe Commerce auf Cloud-Infrastruktur 2.1.2 und höher
* Redis, beliebige Version

## Problem

Ausführen der `setup:static-content:deploy` -Befehl führt zum Fehler &quot;Redis&quot;:

```php
)
[2017-06-02 19:57:59] Command:php ./bin/magento setup:static-content:deploy --jobs=3  en_US

[Exception]

Notice: unserialize(): Error at offset 0 of 1 bytes in /app/<domain>/vendor/magento/module-config/App/Config/Type/System.php
on line 214

.....

[CredisException]
read error on connection

[RedisException]
read error on connection

.....

[Exception]

Notice: unserialize(): Error at offset 0 of 1 bytes in /app/<domain>/vendor/magento/module-config/App/Config/Type/System.php
on line 214

.....

[RuntimeException]
Command php ./bin/magento setup:static-content:deploy --jobs=3  en_US  returned code 3
```

## Ursache

Das Problem wird durch parallele Interferenzprozesse in der Redis-Verbindung verursacht.

Hier ein Prozess in `App/Config/Type/System.php` erwartete eine Antwort für `system_defaultweb`, erhielt jedoch eine Antwort für `system_cache_exists` das durch einen anderen Prozess hergestellt wurde. Weitere Informationen finden Sie unter [Jason Woods Post](https://github.com/magento/magento2/issues/9287#issuecomment-302362283).

## Lösung

Deaktivieren von Parallelismus und Ausführen `setup:static-content:deploy` in einem Einzelthread-Modus durch Festlegen der folgenden Umgebungsvariablen:

```
STATIC_CONTENT_THREADS =1
```

Sie können auch die `setup:static-content:deploy` -Befehl, gefolgt von `-j 1` (oder `--jobs=1`).

>[!NOTE]
>
>Im Einzelthread-Modus kann die Bereitstellung statischer Inhalte viermal länger dauern.

## Weitere Informationen

In unserer Entwicklerdokumentation:

* [Konfigurieren von Redis](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/redis/config-redis.html)
* [Befehlszeilenaktualisierung](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html)
