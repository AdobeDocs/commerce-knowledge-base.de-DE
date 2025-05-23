---
title: Redis-Deserialisierungsfehler „setup:static-content:deploy“
description: Dieser Artikel bietet eine Fehlerbehebung für den Fehler „Redis Deserialize“ bei der Ausführung von „magento setup:static-content:deploy“.
exl-id: 4bc88933-3bf9-4742-b864-b82d3c1b07a9
feature: Cache, Deploy, Page Content, SCD, Services, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Redis-Deserialisierungs-`setup:static-content:deploy`

Dieser Artikel bietet eine Fehlerbehebung für den Fehler „Redis serialize“ bei der Ausführung von `magento setup:static-content:deploy`.

Das Ausführen von `magento setup:static-content:deploy` verursacht den Redis-Fehler:

```
[Exception]
Notice: unserialize(): Error at offset 0 of 1 bytes in
/var/www/domain.com/vendor/magento/module-config/App/Config/Type/System.php on line 214
```

Das Problem wird durch parallele Störvorgänge an der Redis-Verbindung verursacht.

Führen Sie zur Auflösung `setup:static-content:deploy` in einem Einzelthreadmodus aus, indem Sie die folgende Umgebungsvariable festlegen:

```
STATIC_CONTENT_THREADS =1
```

Oder führen Sie den `setup:static-content:deploy`-Befehl aus, gefolgt vom `-j 1`-Argument (oder `--jobs=1` ).

Beachten Sie, dass die Deaktivierung von Multithreading die Bereitstellung statischer Assets verlangsamt.

## Betroffene Versionen

* Adobe Commerce On-Premises: 2.1.2 und höher
* Adobe Commerce auf Cloud-Infrastruktur 2.1.2 und höher
* Redis, beliebige Version

## Problem

Die Ausführung des `setup:static-content:deploy`-Befehls verursacht den Redis-Fehler:

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

Das Problem wird durch parallele, störende Prozesse auf der Redis-Verbindung verursacht.

Hier erwartete ein Prozess in `App/Config/Type/System.php` eine Antwort für `system_defaultweb`, erhielt aber eine Antwort für `system_cache_exists`, die von einem anderen Prozess vorgenommen wurde. Siehe die detaillierte Erklärung in [Jason Woods&#39; Beitrag](https://github.com/magento/magento2/issues/9287#issuecomment-302362283).

## Lösung

Deaktivieren Sie die Parallelität und führen Sie `setup:static-content:deploy` in einem Einzelthreadmodus aus, indem Sie die folgende Umgebungsvariable festlegen:

```
STATIC_CONTENT_THREADS =1
```

Außerdem können Sie den `setup:static-content:deploy`-Befehl ausführen, gefolgt vom `-j 1`-Argument (oder dem `--jobs=1`-Argument).

>[!NOTE]
>
>Im Single-Thread-Modus kann der Bereitstellungsprozess statischer Inhalte viermal länger dauern.

## Weitere Informationen

In unserer Entwicklerdokumentation:

* [Konfigurieren von Redis](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/redis/config-redis.html?lang=de)
* [Befehlszeilen-Upgrade](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html?lang=de)
