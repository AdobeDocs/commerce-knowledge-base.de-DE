---
title: Redis unserialize error `setup:static-content:deploy`
description: Dieser Artikel enthält eine Fehlerbehebung für den Fehler "Redis unserialize", wenn "magento setup:static-content:deploy" ausgeführt wird.
exl-id: 4bc88933-3bf9-4742-b864-b82d3c1b07a9
feature: Cache, Deploy, Page Content, SCD, Services, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Redis unserialize error `setup:static-content:deploy`

Dieser Artikel enthält eine Fehlerbehebung für den Redis-Deserialisierungs-Fehler bei der Ausführung von `magento setup:static-content:deploy`.

Wird `magento setup:static-content:deploy` ausgeführt, wird der Redis-Fehler ausgegeben:

```
[Exception]
Notice: unserialize(): Error at offset 0 of 1 bytes in
/var/www/domain.com/vendor/magento/module-config/App/Config/Type/System.php on line 214
```

Das Problem wird durch parallele Störprozesse in der Redis-Verbindung verursacht.

Führen Sie zum Auflösen `setup:static-content:deploy` in einem Einzelthread-Modus aus, indem Sie die folgende Umgebungsvariable festlegen:

```
STATIC_CONTENT_THREADS =1
```

oder führen Sie den Befehl `setup:static-content:deploy` aus, gefolgt vom Argument `-j 1` (oder `--jobs=1` ).

Beachten Sie, dass das Deaktivieren der Multithreading-Funktion die Bereitstellung statischer Assets verlangsamt.

## Betroffene Versionen

* Adobe Commerce vor Ort: 2.1.2 und höher
* Adobe Commerce auf Cloud-Infrastruktur 2.1.2 und höher
* Redis, beliebige Version

## Problem

Wenn Sie den Befehl `setup:static-content:deploy` ausführen, tritt der Fehler &quot;Redis&quot;auf:

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

Hier erwartete ein Prozess in `App/Config/Type/System.php` eine Antwort für `system_defaultweb`, erhielt jedoch eine Antwort für `system_cache_exists`, die von einem anderen Prozess ausgeführt wurde. Weitere Informationen finden Sie in der detaillierten Erklärung unter [Jason Woods&#39; post](https://github.com/magento/magento2/issues/9287#issuecomment-302362283).

## Lösung

Deaktivieren Sie die Parallelität und führen Sie `setup:static-content:deploy` in einem Einzelthread-Modus aus, indem Sie die folgende Umgebungsvariable festlegen:

```
STATIC_CONTENT_THREADS =1
```

Sie können auch den Befehl `setup:static-content:deploy` gefolgt vom Argument `-j 1` (oder `--jobs=1`) ausführen.

>[!NOTE]
>
>Im Einzelthread-Modus kann die Bereitstellung statischer Inhalte viermal länger dauern.

## Weitere Informationen

In unserer Entwicklerdokumentation:

* [Redis konfigurieren](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/redis/config-redis.html)
* [Befehlszeilenaktualisierung](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html)
