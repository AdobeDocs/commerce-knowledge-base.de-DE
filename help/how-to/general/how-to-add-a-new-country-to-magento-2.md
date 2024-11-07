---
title: Hinzufügen eines neuen Landes zur Adobe Commerce
description: In diesem Artikel wird beschrieben, wie Sie ein Land hinzufügen, das nicht in Adobe Commerce und der Zend Locale Library vorhanden ist. Dies erfordert Code- und Datenbankänderungen, die Kundenanpassungen gemäß Ihren jeweiligen Vertragsbedingungen darstellen. Bitte beachten Sie, dass die in diesem Artikel enthaltenen Beispielmaterialien "AS IS" ohne jegliche Garantie bereitgestellt werden. Weder Adobe noch verbundene Unternehmen sind verpflichtet, diese Materialien zu pflegen, zu korrigieren, zu aktualisieren, zu ändern, zu ändern oder anderweitig zu unterstützen. Hier werden wir die Grundprinzipien beschreiben, was zu tun ist, um dies zu erreichen.
exl-id: af499add-4966-4a3a-972a-62a34c169a1b
feature: Build, Cache
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '1105'
ht-degree: 0%

---

# Hinzufügen eines neuen Landes zur Adobe Commerce

In diesem Artikel wird beschrieben, wie Sie ein Land hinzufügen, das nicht in Adobe Commerce und der Zend Locale Library vorhanden ist. Dies erfordert Code- und Datenbankänderungen, die Kundenanpassungen gemäß Ihren jeweiligen Vertragsbedingungen darstellen. Bitte beachten Sie, dass die in diesem Artikel enthaltenen Beispielmaterialien &quot;AS IS&quot; ohne jegliche Garantie bereitgestellt werden. Weder Adobe noch verbundene Unternehmen sind verpflichtet, diese Materialien zu pflegen, zu korrigieren, zu aktualisieren, zu ändern, zu ändern oder anderweitig zu unterstützen. Hier werden wir die Grundprinzipien beschreiben, was zu tun ist, um dies zu erreichen.

In diesem Beispiel erstellen wir ein neues Adobe Commerce-Modul mit einem Daten-Patch, der bei der Installation oder Aktualisierung von Adobe Commerce angewendet wird, und fügen ein Abstract-Land mit dem Ländercode XX zu Adobe Commerce hinzu. Das Verzeichnis [Adobe Commerce](https://developer.adobe.com/commerce/php/module-reference/module-directory/) erstellt eine erste Länderliste und verwendet dann Setup-Patches, um Gebiete an diese Liste anzuhängen. In diesem Artikel wird erläutert, wie ein neues Modul erstellt wird, das ein neues Land an die Liste anhängt. Sie können den Code des vorhandenen Adobe Commerce Directory-Moduls zur Referenz überprüfen. Dies liegt daran, dass das folgende Beispielmodul den Verzeichnismodulauftrag zum Erstellen einer Liste von Ländern und Regionen fortsetzt und Teile des Codes der Adobe Commerce-Ordnermodul-Setup-Patches wiederverwendet.

## Empfohlene Dokumentation

Sie müssen mit der Entwicklung von Adobe Commerce-Modulen vertraut sein, um eine neue erstellen zu können.

Beachten Sie die folgenden Themen in unserer Entwicklerdokumentation, bevor Sie versuchen, ein neues Modul zu erstellen:

* [PHP-Entwicklerhandbuch](https://developer.adobe.com/commerce/php/development/)
* [Modulübersicht](https://developer.adobe.com/commerce/php/architecture/modules/overview/)
* [Neues Modul erstellen](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/backend-development/create-module)
* [Modulkonfigurationsdateien](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/files/module-files)

## Erforderliche Informationen

Ein neues Land muss in Adobe Commerce über einen eindeutigen Namen, eine Länderkennung, ISO2- und ISO3-Codes verfügen.

## Modulstruktur

In diesem Beispiel wird ein neues Modul namens \`ExtraCountries\` mit der folgenden Verzeichnisstruktur erstellt:

(Weitere Informationen zur Modulstruktur finden Sie unter [Modulübersicht](https://developer.adobe.com/commerce/php/architecture/modules/overview/) in unserer Entwicklerdokumentation).

<pre><ExtraCountries>
 |
 <etc>
 | |
 | config.xml
 | di.xml
 | module.xml
 |
 <Plugin>
 | |
 | <Framework>
 |   |
 |   <Locale>
 |     |
 |     TranslatedListsPlugin.php
 |
 <Setup>
 | |
 | <Patch>
 |   |
 |   <Data>
 |     |
 |     AddDataForAbstractCountry.php
 |
 composer.json
 registration.php</pre>

>[!NOTE]
>
>Jeder Kopfzeilenabschnitt dieses Artikels beschreibt Dateien aus dem Abschnitt zur Modulstruktur.

## ExtraCountries/etc/config.xml

In dieser XML-Datei wird eine neue Modulkonfiguration definiert. Die folgenden Konfigurationen und Tags können bearbeitet werden, um die neuen Standardeinstellungen für Länder anzupassen.

* `allow` - Um das neu hinzugefügte Land standardmäßig der Liste &quot;Länder zulassen&quot;hinzuzufügen, hängen Sie den neuen Ländercode an das Ende des `allow` -Tag-Inhalts an. Ländercodes sind kommagetrennt. Beachten Sie, dass dieses Tag die Daten aus der `Directory`-Modulkonfigurationsdatei *(Directory/etc/config.xml)* `allow` überschreiben wird. Deshalb wiederholen wir alle Codes hier und fügen den neuen hinzu.
* `optional_zip_countries` - Wenn die Postleitzahl für das neu hinzugefügte Land optional sein soll, hängen Sie den Ländercode an das Ende des Inhalts des `optional_zip_countries` -Tags an. Ländercodes sind kommagetrennt. Beachten Sie, dass dieses Tag die Daten aus der `Directory`-Modulkonfigurationsdatei *(Directory/etc/config.xml)* `optional_zip_countries` überschreiben wird. Deshalb wiederholen wir alle Codes hier und fügen den neuen hinzu.
* `eu_countries` - Wenn das neu hinzugefügte Land standardmäßig Teil der Liste der Länder der Europäischen Union sein muss, hängen Sie den Ländercode an das Ende des Inhalts des Tags `eu_countries` an. Ländercodes sind kommagetrennt. Beachten Sie, dass dieses Tag die Daten aus dem Tag `Store` der Modulkonfigurationsdatei *(\_Store/etc/config.xml\_)* `eu_countries` überschreibt. Deshalb wiederholen wir alle Codes hier und fügen den neuen hinzu.
* Beispiel einer Datei `config.xml`

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <default>
        <general>
            <country>
                <!-- append a new country codes to the end of this list -->
                <allow>AF,AL,DZ,AS,AD,AO,AI,AQ,AG,AR,AM,AW,AU,AT,AX,AZ,BS,BH,BD,BB,BY,BE,BZ,BJ,BM,BL,BT,BO,BQ,BA,BW,BV,BR,IO,VG,BN,BG,BF,BI,KH,CM,CA,CD,CV,KY,CF,TD,CL,CN,CX,CW,CC,CO,KM,CG,CK,CR,HR,CU,CY,CZ,DK,DJ,DM,DO,EC,EG,SV,GQ,ER,EE,ET,FK,FO,FJ,FI,FR,GF,PF,TF,GA,GM,GE,DE,GG,GH,GI,GR,GL,GD,GP,GU,GT,GN,GW,GY,HT,HM,HN,HK,HU,IS,IM,IN,ID,IR,IQ,IE,IL,IT,CI,JE,JM,JP,JO,KZ,KE,KI,KW,KG,LA,LV,LB,LS,LR,LY,LI,LT,LU,ME,MF,MO,MK,MG,MW,MY,MV,ML,MT,MH,MQ,MR,MU,YT,FX,MX,FM,MD,MC,MN,MS,MA,MZ,MM,NA,NR,NP,NL,AN,NC,NZ,NI,NE,NG,NU,NF,KP,MP,NO,OM,PK,PW,PA,PG,PY,PE,PH,PN,PL,PS,PT,PR,QA,RE,RO,RS,RU,RW,SH,KN,LC,PM,VC,WS,SM,ST,SA,SN,SC,SL,SG,SK,SI,SB,SO,ZA,GS,KR,ES,LK,SD,SR,SJ,SZ,SE,CH,SX,SY,TL,TW,TJ,TZ,TH,TG,TK,TO,TT,TN,TR,TM,TC,TV,VI,UG,UA,AE,GB,US,UM,UY,UZ,VU,VA,VE,VN,WF,EH,XK,YE,ZM,ZW,XX</allow>
​
                <!-- if added countries need to belong to the European Union Countries list by default, append their codes to the end of this list -->
                <eu_countries>AT,BE,BG,CY,CZ,DK,EE,FI,FR,DE,GR,HR,HU,IE,IT,LV,LT,LU,MT,NL,PL,PT,RO,SK,SI,ES,SE,GB,XX</eu_countries>
​
                <!-- if added countries are not require zip code, append it's code to the end of this list -->
                <optional_zip_countries>HK,IE,MO,PA,GB,XX</optional_zip_countries>
            </country>
        </general>
    </default>
</config>
```

Weitere Informationen zu den Modulkonfigurationsdateien finden Sie im [PHP-Entwicklerhandbuch > Konfigurationsdateien definieren](https://developer.adobe.com/commerce/php/development/build/required-configuration-files/) in unserer Entwicklerdokumentation.

Beachten Sie, dass diese Änderungen optional sind und sich nur auf die Standardzugehörigkeit des neuen Landes zu den Listen &quot;Länder zulassen&quot;, &quot;Postleitzahl ist optional für&quot;und &quot;Länder der Europäischen Union&quot;auswirken. Wenn diese Datei aus der Modulstruktur übersprungen wird, wird weiterhin ein neues Land hinzugefügt, es muss jedoch manuell auf der Einstellungsseite **Admin** > **Geschäfte** > *Einstellungen* > **Konfiguration** > **Allgemein** > **Länderoptionen** konfiguriert werden.

### ExtraCountries/etc/di.xml

Die Datei `di.xml` konfiguriert, welche Abhängigkeiten vom Objektmanager eingefügt werden. Weitere Informationen zu `di.xml` finden Sie unter <a>PHP Developer Guide > The di.xml</a> in unserer Entwicklerdokumentation.

In unserem Beispiel müssen wir einen `_TranslatedListsPlugin_` registrieren, der neu eingeführte Ländercodes in vollständige Ländernamen übersetzt, wenn in den Lokalisierungsdaten der Zend Locale Library keine Codes vorhanden sind.

Beispiel für `di.xml`

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Magento\Framework\Locale\TranslatedLists">
        <plugin name="Magento_Directory" type="VendorName\ExtraCountries\Plugin\Framework\Locale\TranslatedListsPlugin"/>
    </type>
</config>
```

### ExtraCountries/etc/module.xml

In der Modulregistrierungsdatei müssen wir die Abhängigkeit für das Modul &quot;Adobe Commerce Directory&quot; angeben, um sicherzustellen, dass das Modul &quot;Extra Countries&quot; registriert und nach dem Verzeichnismodul ausgeführt wird.

Weitere Informationen zu Modulabhängigkeiten finden Sie unter [Verwalten von Modulabhängigkeiten](https://developer.adobe.com/commerce/php/architecture/modules/dependencies/#managing-module-dependencies) in unserer Entwicklerdokumentation.

Beispiel für `module.xml`

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
    <module name="VendorName_ExtraCountries" >
        <sequence>
            <module name="Magento_Directory"/>
        </sequence>
    </module>
</config>
```

### ExtraCountries/Plugin/Framework/Locale/TranslatedListsPlugin.php

In der Plug-in-Methode `aroundGetCountryTranslation()` müssen wir einen Ländercode in einen vollständigen Ländernamen übersetzen. Dies ist ein erforderlicher Schritt für Länder, denen kein vollständiger Name mit einem neuen Ländercode in der Zend Locale Library zugeordnet ist.

```php
<?php
namespace VendorName\ExtraCountries\Plugin\Framework\Locale;
​
use Magento\Framework\Locale\ListsInterface;
​
/**
 * Plugin to add full names of added countries that are not included in Zend Locale Data
 */
class TranslatedListsPlugin
{
    /**
     * Get the full name of added countries
     *
     * Since the locale data for the added country may not be present in the Zend Locale Library,
     * we need to provide full country name matching the added code
     *
     * @param ListsInterface $subject
     * @param callable $proceed
     * @param $value
     * @param null $locale
     * @return string
     */
    public function aroundGetCountryTranslation(
        ListsInterface $subject,
        callable $proceed,
        $value,
        $locale = null
    )
    {
        if ($value == 'XX') {
            return 'Abstract Country';
        }
​
        return $proceed($value, $locale);
    }
}
```

### ExtraCountries/Setup/Patch/Data/AddDataForAbstractCountry.php

Dieser Datenpatch wird während der Installation/Aktualisierung von Adobe Commerce ausgeführt und fügt einen neuen Länderdatensatz zur Datenbank hinzu.

Weitere Informationen zu Daten-Patches finden Sie unter [Entwickeln von Daten- und Schema-Patches](https://developer.adobe.com/commerce/php/development/components/declarative-schema/patches/) in unserer Entwicklerdokumentation.

Im folgenden Beispiel sehen Sie, dass das Array `$data` der Methode `apply()` Länderkennungen, ISO2- und ISO3-Codes für das neue Land enthält und diese Daten in die Datenbank eingefügt werden.

```php
<?php
namespace Magento\ExtraCountries\Setup\Patch\Data;
​
use Magento\Framework\Setup\ModuleDataSetupInterface;
use Magento\Framework\Setup\Patch\DataPatchInterface;
use Magento\Framework\Setup\Patch\PatchVersionInterface;
​
/**
 * Add Abstract Country data to the country list
 *
 * @package Magento\ExtraCountries\Setup\Patch
 */
class AddDataForAbstractCountry implements DataPatchInterface, PatchVersionInterface
{
    /**
     * @var ModuleDataSetupInterface
     */
    private $moduleDataSetup;
​
    /**
     * @param ModuleDataSetupInterface $moduleDataSetup
     */
    public function __construct(
        ModuleDataSetupInterface $moduleDataSetup
    ) {
        $this->moduleDataSetup = $moduleDataSetup;
    }
​
    /**
     * @inheritdoc
     */
    public function apply()
    {
        /**
         * Fill table directory/country
         */
        $data = [
            ['XX', 'XX', 'XX']
        ];
​
        $columns = ['country_id', 'iso2_code', 'iso3_code'];
        $this->moduleDataSetup->getConnection()->insertArray(
            $this->moduleDataSetup->getTable('directory_country'),
            $columns,
            $data
        );
    }
​
    /**
     * @inheritdoc
     */
    public static function getDependencies()
    {
        return [];
    }
​
    /**
     * @inheritdoc
     */
    public static function getVersion()
    {
        return '0.0.1';
    }
​
    /**
     * @inheritdoc
     */
    public function getAliases()
    {
        return [];
    }
}
```

### ExtraCountries/registration.php

Dies ist ein Beispiel für die Datei registration.php . Weitere Informationen zur Modulregistrierung finden Sie im [PHP-Entwicklerhandbuch > Registrieren Ihrer Komponente](https://developer.adobe.com/commerce/php/development/build/component-registration/) in unserer Entwicklerdokumentation.

```php
<?php
use Magento\Framework\Component\ComponentRegistrar;
​
ComponentRegistrar::register(ComponentRegistrar::MODULE, 'VendorName_ExtraCountries', __DIR__);
```

### ExtraCountries/composer.json

Dies ist ein Beispiel für die Datei &quot;composer.json&quot;.

Weitere Informationen zu Composer.json finden Sie im [PHP-Entwicklerhandbuch > Die Datei &quot;Composer.json&quot;](https://developer.adobe.com/commerce/php/development/build/composer-integration/) in unserer Entwicklerdokumentation.

```json
{
    "name": "vendor_name/module-extra-countries",
    "description": "A module that adds extra countries to magento directory",
    "type": "magento2-module",
    "license": [
    ],
    "require": {
        "php": "~7.3.0||~7.4.0",
        "lib-libxml": "*",
        "magento/framework": "*",
        "magento/module-directory": "*"
    },
    "autoload": {
        "files": [
            "registration.php"
        ],
        "psr-4": {
            "VendorName\\ExtraCountries\\": ""
        }
    },
    "config": {
        "sort-packages": true
    }
}
```

## Modulinstallation

Informationen zum Installieren des Moduls finden Sie unter [Modulspeicherorte](https://developer.adobe.com/commerce/php/architecture/modules/overview/#module-locations) in unserer Entwicklerdokumentation.

Sobald sich das Modulverzeichnis an einem richtigen Speicherort befindet, führen Sie `bin/magento setup:upgrade` aus, um die Datenpatches anzuwenden und das Übersetzungs-Plug-in zu registrieren.

Möglicherweise müssen Sie den Browser-Cache bereinigen, damit die neuen Änderungen funktionieren.
