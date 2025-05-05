---
title: PHP mcrypt-Erweiterung nicht richtig installiert
description: PHP mcrypt-Erweiterung nicht richtig installiert
exl-id: 1010349e-6631-4a05-8883-5cc903d67534
feature: Extensions, Install
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# PHP mcrypt-Erweiterung nicht richtig installiert

>[!WARNING]
>
>BITTE BEACHTEN SIE: Die mcrypt-Bibliotheksfunktion wurde [veraltet ab PHP 7.1 und aus PHP 7.2 entfernt](https://www.php.net/manual/en/intro.mcrypt.php).

## Detail

Fehler können Folgendes umfassen:

```php
exception 'Exception' with message 'PHP Warning: PHP Startup: Unable to load dynamic library '/usr/lib/php5/20121212/mcrypt.so' - /usr/lib/php5/20121212/mcrypt.so: cannot open shared object file: No such file or directory
```

```php
Installing data fixtures:
/usr/bin/php -f '/Users/username/www/magento/dev/shell/run_data_fixtures.php' -- --bootstrap='MAGE_DIRS[base][path]=/Users/username/www/magento' 2>&1
[ERROR] exception 'Exception' with message '
Fatal error: Uncaught exception 'Exception' with message 'Module 'Magento_Core' depends on 'mcrypt' PHP [extension](https://experienceleague.adobe.com/de/docs/commerce-operations/operational-playbook/glossary#extension) that is not loaded.'
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

Insbesondere bei Entwicklersystemen, die einen vom Betriebssystem getrennten „Stack“ aus Linux/Apache/MySQL/PHP (LAMP) enthalten, ist es möglich, dass mcrypt entweder gar nicht oder nur im Pfad des LAMP-Stacks, nicht aber im Pfad des Betriebssystems installiert ist.

Daher kann das Adobe Commerce-Installationsprogramm die Erweiterung nicht finden, und die Installation schlägt fehl.

## Vorschlag

Stellen Sie fest, ob die mcrypt-Erweiterung auf eine der folgenden Arten geladen wird:

* Richten Sie eine [phpinfo.php](http://kb.mediatemple.net/questions/764/How+can+I+create+a+phpinfo.php+page%3F#gs)-Datei im Stammverzeichnis des Webservers ein und untersuchen Sie die Ausgabe in einem Webbrowser.
* Führen Sie den folgenden Befehl aus:    `$ php -r "phpinfo();" | grep mcrypt`

Wenn mcrypt *nicht* installiert ist, werden Meldungen ähnlich der folgenden angezeigt:

```php
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20121212/mcrypt.so' - /usr/lib/php5/20121212/mcrypt.so: cannot open shared object file: No such file or directory in Unknown on line 0
```

In einigen Fällen müssen Sie möglicherweise die Adobe Commerce-Software über die [Befehlszeile](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/advanced) installieren und den vollständigen Pfad zum LAMP-Stack angeben, auf dem mcrypt installiert ist.
