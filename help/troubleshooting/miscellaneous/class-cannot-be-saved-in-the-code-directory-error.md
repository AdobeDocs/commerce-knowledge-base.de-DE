---
title: Fehler „Klasse kann nicht im Codeverzeichnis gespeichert werden“
description: In diesem Artikel wird beschrieben, wie Sie das Problem beheben können, dass die Art und Weise, wie Sie Abhängigkeiten angegeben haben, verhindert, dass Klassen automatisch im laufenden Betrieb generiert werden, und Sie die Fehlermeldung *„Klasse kann nicht im Verzeichnis "/code“ gespeichert werden.
exl-id: e2c00d4d-31c3-4446-a317-a8ac92c707d5
feature: Configuration
role: Developer
source-git-commit: 139c2836ba36686357c7a5458a36550c7b1273c1
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# Fehler „Klasse kann nicht im Codeverzeichnis gespeichert werden“

In diesem Artikel wird beschrieben, wie Sie das Problem beheben können, dass die Art und Weise, wie Sie Abhängigkeiten angegeben haben, verhindert, dass Klassen automatisch im laufenden Betrieb generiert werden, und Sie die Fehlermeldung *Klasse kann nicht im Verzeichnis &quot;/code“ gespeichert*.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.2.0 oder höher

## Problem

<u>Schritte zur Reproduktion</u>

1. Schreiben Sie in Ihrer lokalen Umgebung eine benutzerdefinierte Klasse mit einer Abhängigkeit von der automatisch generierten Klasse.
1. Führen Sie das Szenario aus, in dem die benutzerdefinierte Klasse ausgelöst wird, und sehen Sie, wie sie ordnungsgemäß funktioniert.
1. Übergeben Sie Ihre Änderungen und übertragen Sie sie in die Integrationsumgebung. Dadurch würde der Bereitstellungsprozess Trigger. Die Bereitstellung war erfolgreich.
1. Führen Sie in [Integrationsumgebung](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27242) das Szenario aus, in dem Ihre benutzerdefinierte Klasse ausgelöst wird.

<u>Erwartetes Ergebnis</u>

Alles funktioniert wie in Ihrer lokalen Umgebung.

<u>Tatsächliches Ergebnis</u>

Fehler mit der Fehlermeldung, dass die Klasse nicht im `generated/code` gespeichert werden kann.

## Ursache

Die Ursache des Problems besteht darin, dass die Klasse, von der Sie abhängig sind, während der Bereitstellung nicht generiert wird und beim Auslösen der Klasse nicht später spontan generiert werden kann, da das `generated/code` nach Abschluss der Bereitstellung nicht zum Schreiben verfügbar ist.

Dafür gibt es zwei Hauptgründe:

* &#x200B;1. Fall: Die Klasse mit Abhängigkeiten von automatisch generierten Klassen befindet sich im Einstiegspunkt (z. B. `index.php` ), der während der Bereitstellung nicht auf Abhängigkeiten überprüft wird.
* &#x200B;2. Fall: Die Abhängigkeit von der automatisch generierten Klasse wird direkt angegeben (im Vergleich zur empfohlenen Verwendung des -Konstruktors zum Deklarieren der Abhängigkeit).

## Lösung

Eine gemeinsame Lösung für beide Fälle wäre die Erstellung einer echten Factory anstelle der automatisch generierten Klasse.

Oder es gibt für jeden Fall eine bestimmte Lösung.

### Fallspezifische Lösung 1

Verschieben Sie den Klassencode vom Einstiegspunkt in ein separates Modul und verwenden Sie ihn dann im Einstiegspunkt.

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

Sie müssen die folgenden Schritte ausführen:

1. Klassendefinition nach `app/code/YourVendor/YourModule` verschieben:

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

### Case 2-spezifische Lösung

Verschiebt die Abhängigkeitsdeklaration in den Konstruktor.

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

* [Code-Generierung](https://developer.adobe.com/commerce/php/development/components/code-generation/) in unserer Entwicklerdokumentation.
