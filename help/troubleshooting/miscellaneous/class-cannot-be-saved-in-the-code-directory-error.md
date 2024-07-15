---
title: Fehler "Klasse kann nicht im Codeverzeichnis gespeichert werden"
description: In diesem Artikel wird beschrieben, wie Sie das Problem beheben, bei dem die Art und Weise, wie Sie Abhängigkeiten angegeben haben, verhindert, dass Klassen dynamisch automatisch generiert werden und Sie die Fehlermeldung *"Klasse kann nicht im generierten/Code-Verzeichnis gespeichert werden"* erhalten.
exl-id: e2c00d4d-31c3-4446-a317-a8ac92c707d5
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# Fehler &quot;Klasse kann nicht im Codeverzeichnis gespeichert werden&quot;

In diesem Artikel wird beschrieben, wie Sie das Problem beheben, bei dem die Art und Weise, wie Sie Abhängigkeiten angegeben haben, verhindert, dass Klassen dynamisch automatisch generiert werden und Sie die Fehlermeldung *&quot;Klasse kann nicht im generierten/Codeverzeichnis gespeichert werden&quot;* erhalten.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.2.0 oder höher

## Problem

<u>Zu reproduzierende Schritte</u>

1. Schreiben Sie in Ihrer lokalen Umgebung eine benutzerdefinierte Klasse mit einer Abhängigkeit von der automatisch generierten Klasse.
1. Führen Sie das Szenario aus, in dem Ihre benutzerdefinierte Klasse ausgelöst wird, und überprüfen Sie, ob sie ordnungsgemäß funktioniert.
1. Übernehmen Sie Ihre Änderungen und übertragen Sie sie in die Integrationsumgebung. Dies würde den Bereitstellungsprozess Trigger. Die Implementierung ist erfolgreich.
1. Führen Sie in der [Integrationsumgebung](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) das Szenario aus, in dem Ihre benutzerdefinierte Klasse ausgelöst wird.

<u>Erwartetes Ergebnis</u>

Alles funktioniert ordnungsgemäß, genauso wie in Ihrer lokalen Umgebung.

<u>Tatsächliches Ergebnis</u>

Fehler mit der Fehlermeldung, dass Ihre Klasse nicht im Verzeichnis `generated/code` gespeichert werden kann.

## Ursache

Die Ursache des Problems ist, dass die Klasse, von der Sie abhängig sind, während der Bereitstellung nicht generiert wird und später nicht sofort generiert werden kann, wenn die Klasse ausgelöst wird, da das Verzeichnis `generated/code` nach Abschluss der Bereitstellung nicht zum Schreiben verfügbar ist.

Es gibt zwei Hauptgründe dafür:

* Fall 1: Die Klasse mit Abhängigkeiten von automatisch generierten Klassen befindet sich im Einstiegspunkt (wie `index.php` ), der während der Bereitstellung nicht auf Abhängigkeiten überprüft wird.
* Fall 2: Die Abhängigkeit zur automatisch generierten Klasse wird direkt angegeben (im Vergleich zur empfohlenen Verwendung des Konstruktors zum Deklarieren der Abhängigkeit).

## Lösung

Eine gängige Lösung für beide Fälle wäre die Schaffung einer echten Fabrik anstelle der automatisch generierten Klasse.

Oder es gibt für jeden Fall eine bestimmte Lösung.

### Fall-1-spezifische Lösung

Verschieben Sie Ihren Klassencode vom Einstiegspunkt in ein separates Modul und verwenden Sie ihn dann im Einstiegspunkt.

<u>Beispiel</u>

Originalcode in, z. B. `index2.php` :

```php
<?php
use YourVendor\SomeModule\Model\GeneratedFactory;

require realpath(__DIR__) . '/../app/bootstrap.php';
$bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);

class SomeClass
{
    private $generatedFactory;

    public function __construct(GeneratedFactory $generatedFactory)
    {
        $this->generatedFactory = $generatedFactory;
    }

// Some code here...
}

$someObject = $bootstrap->getObjectManager()->create(SomeClass::class);

// There is some code that uses $someObject
```

Führen Sie die folgenden Schritte aus:

1. Verschieben Sie die Klassendefinition auf `app/code/YourVendor/YourModule`:

   ```php
      <?php
       namespace YourVendor\YourModule;
       use YourVendor\YourModule\Model\GeneratedFactory;
       class YourClass
       {
           private $generatedFactory;
   
           public function __construct(GeneratedFactory $generatedFactory)
           {
               $this->generatedFactory = $generatedFactory;
           }
       // Some code here...
       }
   ```

1. Bearbeiten Sie den Einstiegspunkt `my_api/index.php` so, dass er wie folgt aussieht:

   ```php
     <?php
     use YourVendor\YourModule\YourClass;
         require realpath(__DIR__) . '/../app/bootstrap.php';
         $bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);
         $someObject = $bootstrap->getObjectManager()->create(YourClass::class);
     // Some code using $someObject
   ```

### Fall 2 - spezifische Lösung

Verschieben Sie die Abhängigkeitsdeklaration in den Konstruktor.

<u>Beispiel</u>

Ursprüngliche Klassendeklaration:

```php
<?php
namespace YourVendor\YourModule;

use YourVendor\SomeModule\Model\GeneratedFactory;
use Magento\Framework\App\ObjectManager;

class YourClass
{
    private $generatedFactory;
    private $someParam;

    public function __construct($someParam)
    {
        $this--->someParam = $someParam;
        $this->generatedFactory = ObjectManager::getInstance()->get(GeneratedFactory::class);
    }

    // Some code here...
}
```

Sie müssen den Konstruktor wie folgt ändern:

```php
<?php
namespace YourVendor\YourModule;

use YourVendor\YourModule\Model\GeneratedFactory;
use Magento\Framework\App\ObjectManager;

class YourClass
{
    private $generatedFactory;
    private $someParam;

    public function __construct($someParam, GeneratedFactory $generatedFactory = null)
    {
        $this->someParam = $someParam;
        $this->generatedFactory = $generatedFactory ?: ObjectManager::getInstance()->get(GeneratedFactory::class);
    }

    // Some code here...
}
```

## Verwandtes Lesen

* [Codegenerierung](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/code-generation.html) in unserer Entwicklerdokumentation.
