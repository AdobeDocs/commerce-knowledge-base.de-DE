---
title: PHP mcrypt-Erweiterung nicht ordnungsgemäß installiert
description: PHP mcrypt-Erweiterung nicht ordnungsgemäß installiert
exl-id: 1010349e-6631-4a05-8883-5cc903d67534
feature: Extensions, Install
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# PHP mcrypt-Erweiterung nicht ordnungsgemäß installiert

>[!WARNING]
>
>BITTE BEACHTEN SIE: Die mcrypt-Bibliotheksfunktion war [veraltet von PHP 7.1 und wurde aus PHP 7.2](https://www.php.net/manual/en/intro.mcrypt.php) entfernt.

## Detail

Fehler können Folgendes umfassen:

```php
exception 'Exception' with message 'PHP Warning: [PHP](https://glossary.magento.com/php) Startup: Unable to load dynamic [library](https://glossary.magento.com/library) '/usr/lib/php5/20121212/mcrypt.so' - /usr/lib/php5/20121212/mcrypt.so: cannot open shared object file: No such file or directory
```

```php
Installing data fixtures:
/usr/bin/php -f '/Users/username/www/magento/dev/shell/run_data_fixtures.php' -- --bootstrap='MAGE_DIRS[base][path]=/Users/username/www/magento' 2>&1
[ERROR] [exception](https://glossary.magento.com/exception) 'Exception' with message '
Fatal error: Uncaught exception 'Exception' with message 'Module 'Magento_Core' depends on 'mcrypt' PHP [extension](https://glossary.magento.com/extension) that is not loaded.'
```

```php
======================================================================
   The application has thrown an exception!
======================================================================
 Magento\Framework\Exception
 Command returned non-zero exit code:
`/usr/bin/php5 -f '/var/www/magento2/dev/shell/run_data_fixtures.php' -- --bootstrap='MAGE_DIRS[base][path]=/var/www/magento2' 2>&1`
```

## Beschreibung

Insbesondere auf Entwicklersystemen, die einen von dem Betriebssystem getrennten &quot;Stack&quot;von Linux/Apache/MySQL/PHP (LAMP) enthalten, ist es möglich, dass mcrypt entweder überhaupt nicht installiert ist oder im Pfad des LAMP-Stacks installiert ist, aber nicht im Pfad des Betriebssystems.

Daher kann das Adobe Commerce-Installationsprogramm die Erweiterung nicht finden und die Installation schlägt fehl.

## Empfehlung

Stellen Sie fest, ob die Mcrypt-Erweiterung auf eine der folgenden Arten geladen wird:

* Richten Sie eine [phpinfo.php](http://kb.mediatemple.net/questions/764/How+can+I+create+a+phpinfo.php+page%3F#gs) -Datei im Stammverzeichnis des Webservers ein und untersuchen Sie die Ausgabe in einem Webbrowser.
* Führen Sie den folgenden Befehl aus:    `$ php -r "phpinfo();" | grep mcrypt`

Wenn mcrypt *nicht* installiert ist, werden Meldungen ähnlich der folgenden angezeigt:

```php
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20121212/mcrypt.so' - /usr/lib/php5/20121212/mcrypt.so: cannot open shared object file: No such file or directory in Unknown on line 0
```

In einigen Fällen müssen Sie möglicherweise die Adobe Commerce-Software über die [Befehlszeile](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli.html) installieren und den vollständigen Pfad zum installierten LAMP-Stapel angeben.
