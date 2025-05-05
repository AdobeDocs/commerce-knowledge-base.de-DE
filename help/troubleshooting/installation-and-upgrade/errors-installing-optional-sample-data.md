---
title: Fehler beim Installieren optionaler Beispieldaten
description: In diesem Abschnitt werden Lösungen für Fehler bei der Installation optionaler Beispieldaten beschrieben.
exl-id: 14692e3a-188c-45f1-9df5-ac873cc9eff0
feature: Console, Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# Fehler beim Installieren optionaler Beispieldaten

In diesem Abschnitt werden Lösungen für Fehler bei der Installation optionaler Beispieldaten beschrieben.

## Symptom (Dateisystemberechtigungen)

Fehler im Konsolenprotokoll während der Installation von Beispieldaten mithilfe des Setup-Assistenten:

```php
Module 'Magento_CatalogRuleSampleData':
[ERROR] exception 'Magento\Framework\Exception\LocalizedException' with message 'Can't create directory /var/www/html/magento2/generated/code/Magento/CatalogRule/Model/.' in /var/www/html/magento2/lib/internal/Magento/Framework/Code/Generator.php:103

(more)

Next exception 'ReflectionException' with message 'Class Magento\CatalogRule\Model\RuleFactory does not exist' in /var/www/html/magento2/lib/internal/Magento/Framework/Code/Reader/ClassReader.php:29

(more)
```

Diese Ausnahmen resultieren aus den Einstellungen für Dateisystemberechtigungen.

### Lösung

[Legen Sie die Eigentümerschaft und Berechtigungen des Dateisystems erneut ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html?lang=de), als Benutzer mit `root` Berechtigungen.

## Symptom (Produktionsmodus)

Wenn Sie derzeit für den [Produktionsmodus) eingestellt sind](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html?lang=de) schlägt die Installation der Beispieldaten fehl, wenn Sie den Befehl [magento sampledata:deploy](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/sample-data/composer-packages.html?lang=de) verwenden:

```php
PHP Fatal error: Uncaught TypeError: Argument 1 passed to Symfony\Component\Console\Input\ArrayInput::__construct() must be of the type array, object given, called in /<path>/vendor/magento/framework/ObjectManager/Factory/AbstractFactory.php on line 97 and defined in /<path>/vendor/symfony/console/Symfony/Component/Console/Input/ArrayInput.php:37
```

### Lösung

Installieren Sie keine Beispieldaten im Produktionsmodus. Wechseln Sie in den Entwicklermodus, löschen Sie einige `var` Verzeichnisse und versuchen Sie es erneut.

Geben Sie die folgenden Befehle in der Reihenfolge ein, die als Eigentümer des Dateisystems [Adobe Commerce angezeigt wird](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/file-system/overview.html?lang=de):

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

Deaktivieren Sie während der Installation der Beispieldaten SELinux mithilfe einer Ressource wie der folgenden:

* [www.ibm.com](https://www.ibm.com/docs/ja/ahts/4.0?topic=t-disabling-selinux)
* [Dokumentation zu CentOS](https://docs.centos.org/en-US/docs/)

## Symptom (Verzweigung entwickeln)

Andere Fehler werden angezeigt, z. B.:

```php
[Magento\Setup\SampleDataException] Error during sample data installation: Class Magento\Sales\Model\Service\OrderFactory does not exist
```

### Lösung

Es gibt bekannte Probleme bei der Verwendung von Beispieldaten mit der Adobe Commerce-Entwicklungsverzweigung. Verwenden Sie stattdessen die primäre Verzweigung. Sie können wie folgt zur primären Verzweigung wechseln:

```php
cd <magento_root>
git checkout master
git pull origin master
```

## Symptom (max_execution_time)

Die Installation wird angehalten, bevor die Installation der Beispieldaten abgeschlossen ist. Es folgt ein Beispiel:

```php
(more)

Module 'Magento_CustomerSampleData':
Installing data...
```

Die Installation der Beispieldaten ist noch nicht abgeschlossen.

Dieser Fehler tritt auf, wenn die konfigurierte maximale Ausführungszeit Ihrer PHP-Skripte überschritten wird. Da das Laden von Beispieldaten sehr lange dauern kann, können Sie den Wert während der Installation erhöhen.

### Lösung

Wenn Sie ein Benutzer mit `root` Berechtigungen sind, ändern Sie `php.ini`, um den Wert von `max_execution_time` auf 600 oder mehr zu erhöhen. (600 Sekunden sind 10 Minuten. Sie können den Wert nach Belieben erhöhen.) Sie sollten `max_execution_time` nach erfolgreicher Installation wieder auf den vorherigen Wert zurücksetzen.

Wenn Sie nicht sicher sind, wo sich `php.ini` befindet, geben Sie den folgenden Befehl ein:

```php
php --ini
```

Der Wert von `Loaded Configuration File` ist der `php.ini`, den Sie ändern müssen.

>[!NOTE]
>
>Wir sind uns bewusst, dass dieser Artikel immer noch branchenübliche Softwarebegriffe enthalten kann, die manche als rassistisch, sexistisch oder repressiv empfinden und die den Leser verletzen, traumatisieren oder unwillkommen machen können. Adobe arbeitet daran, diese Begriffe aus unserem Code, unserer Dokumentation und unseren Benutzererlebnissen zu entfernen.
