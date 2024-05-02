---
title: Fehler beim Installieren optionaler Beispieldaten
description: In diesem Thema werden Lösungen für Fehler besprochen, bei denen die Installation optionaler Beispieldaten auftreten kann.
exl-id: 14692e3a-188c-45f1-9df5-ac873cc9eff0
feature: Console, Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# Fehler beim Installieren optionaler Beispieldaten

In diesem Thema werden Lösungen für Fehler besprochen, bei denen die Installation optionaler Beispieldaten auftreten kann.

## Symptom (Dateisystemberechtigungen)

Fehler im Konsolenprotokoll während der Installation der Beispieldaten mithilfe des Einrichtungs-Assistenten:

```php
Module 'Magento_CatalogRuleSampleData':
[ERROR] exception 'Magento\Framework\Exception\LocalizedException' with message 'Can't create directory /var/www/html/magento2/generated/code/Magento/CatalogRule/Model/.' in /var/www/html/magento2/lib/internal/Magento/Framework/Code/Generator.php:103

(more)

Next exception 'ReflectionException' with message 'Class Magento\CatalogRule\Model\RuleFactory does not exist' in /var/www/html/magento2/lib/internal/Magento/Framework/Code/Reader/ClassReader.php:29

(more)
```

Diese Ausnahmen ergeben sich aus den Einstellungen für Dateisystemberechtigungen.

### Lösung

[Legen Sie die Berechtigungen für das Dateisystem erneut fest.](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html) als Benutzer mit `root` -Berechtigungen.

## Symptom (Produktionsmodus)

Wenn Sie derzeit für [Produktionsmodus](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html), schlägt die Installation der Beispieldaten fehl, wenn Sie [Magento-Beispieldaten:deploy](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/sample-data/composer-packages.html) command:

```php
PHP Fatal error: Uncaught TypeError: Argument 1 passed to Symfony\Component\Console\Input\ArrayInput::__construct() must be of the type array, object given, called in /<path>/vendor/magento/framework/ObjectManager/Factory/AbstractFactory.php on line 97 and defined in /<path>/vendor/symfony/console/Symfony/Component/Console/Input/ArrayInput.php:37
```

### Lösung

Installieren Sie keine Beispieldaten im Produktionsmodus. Wechseln Sie in den Entwicklermodus und löschen Sie einige `var` und versuchen Sie es erneut.

Geben Sie die folgenden Befehle in der Reihenfolge ein, die als [Adobe Commerce-Dateisysteminhaber](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/file-system/overview.html):

```php
cd <magento_root>
bin/magento deploy:mode:set developer
rm -rf generated/code/* generated/metadata/*
bin/magento sampledata:deploy
```

## Symptom (Sicherheit)

Während der Installation optionaler Beispieldaten wird eine Meldung ähnlich der folgenden angezeigt:

```php
PHP Fatal error: Call to undefined method Magento\Catalog\Model\Resource\Product\Interceptor::getWriteConnection() in /var/www/magento2/app/code/Magento/SampleData/Module/Catalog/Setup/Product/Gallery.php on line 144
```

### Lösung

Deaktivieren Sie während der Installation der Beispieldaten SELinux mit einer Ressource wie:

* [www.ibm.com](https://www.ibm.com/docs/ja/ahts/4.0?topic=t-disabling-selinux)
* [Dokumentation zu CentOS](https://docs.centos.org/en-US/docs/)

## Symptom (Entwicklungszweig)

Andere Fehler werden angezeigt, z. B.:

```php
[Magento\Setup\SampleDataException] Error during sample data installation: Class Magento\Sales\Model\Service\OrderFactory does not exist
```

### Lösung

Es gibt bekannte Probleme bei der Verwendung von Beispieldaten mit der Adobe Commerce-Entwicklungsverzweigung. Verwenden Sie stattdessen die Masterverzweigung. Sie können wie folgt zur Masterverzweigung wechseln:

```php
cd <magento_root>
git checkout master
git pull origin master
```

## Symptom (max_execution_time)

Die Installation wird beendet, bevor die Beispieldateninstallation abgeschlossen ist. Ein Beispiel:

```php
(more)

Module 'Magento_CustomerSampleData':
Installing data...
```

Die Installation der Beispieldaten ist nicht abgeschlossen.

Dieser Fehler tritt auf, wenn die maximale konfigurierte Ausführungszeit Ihrer PHP-Skripte überschritten wird. Da das Laden von Beispieldaten lange dauern kann, können Sie den Wert während der Installation erhöhen.

### Lösung

Als Benutzer mit `root` Berechtigungen, ändern `php.ini` um den Wert von `max_execution_time` auf 600 oder mehr. (600 Sekunden sind 10 Minuten. Sie können den Wert beliebig erhöhen.) Sie sollten `max_execution_time` zurück zum vorherigen Wert, nachdem die Installation erfolgreich war.

Wenn Sie sich nicht sicher sind, wo `php.ini` befindet, geben Sie den folgenden Befehl ein:

```php
php --ini
```

Der Wert von `Loaded Configuration File` ist die `php.ini` müssen Sie ändern.

>[!NOTE]
>
>Wir wissen, dass dieser Artikel immer noch branchenübliche Softwarebegriffe enthalten kann, die einige rassistisch, sexistisch oder unterdrückend finden und die den Leser verletzen, traumatisiert oder unerwünscht machen können. Adobe arbeitet daran, diese Begriffe aus unserem Code, unserer Dokumentation und unseren Benutzererlebnissen zu entfernen.
