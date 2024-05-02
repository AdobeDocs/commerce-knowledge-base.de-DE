---
title: Fehlerbehebung bei Problemen mit dem Schnellcheckout
description: In diesem Artikel werden Probleme erläutert, die bei der Verwendung der Erweiterung "Quick Checkout für Adobe Commerce"auftreten können, und es werden Lösungen zur Behebung dieser Probleme bereitgestellt, damit Sie die Erweiterung erfolgreich verwenden können.
exl-id: 8ab46318-d62a-4b7e-bbe5-4c52cfeb9e36
feature: Checkout, Orders
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Fehlerbehebung bei Problemen mit dem Schnellcheckout

In diesem Artikel werden Probleme erläutert, die bei der Verwendung der Erweiterung &quot;Quick Checkout für Adobe Commerce&quot;auftreten können, und es werden Lösungen zur Behebung dieser Probleme bereitgestellt, damit Sie die Erweiterung erfolgreich verwenden können.

## Betroffene Produkte und Versionen

* Die [Quick Checkout](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/overview.html) ist sowohl mit Magento Open Source als auch mit Adobe Commerce kompatibel. Siehe [Lebenszyklusrichtlinie](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html) Weitere Informationen zu unterstützten Versionen.

## Falsche Composer-Schlüssel und minimale Stabilität auf `RC`

<u>Ursache</u>:

Wenn die folgende Fehlermeldung angezeigt wird, sind möglicherweise falsche Composer-Schlüssel vorhanden:

```terminal
Could not find a matching version of package magento/quick-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (RC).
```

<u>Lösung</u>:

Überprüfen Sie, ob Ihre Composer-Schlüssel mit dem _Magento-ID_ wird während der Schnellcheckout-Registrierung verwendet.

So sehen Sie, welche Composer-Schlüssel konfiguriert sind:

1. Suchen Sie den Speicherort der `auth.json` Datei:

   ```bash
   composer config --global home
   ```

1. Anzeigen der `auth.json` Datei:

   ```bash
   cat /path/to/auth.json
   ```

1. Siehe [welche Schlüssel Ihrer Magento-ID zugeordnet sind](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

1. Setzen Sie die Mindeststabilität auf `RC` im `composer.json` -Datei.

   ```json
   "minimum-stability": "RC"
   ```

## Nicht genügend Speicher für PHP

<u>Ursache</u>:

Wenn Sie die folgende Fehlermeldung sehen, dass Sie nicht genügend Speicher für PHP haben:

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

<u>Lösung</u>:

[Erhöhen Sie die Speicherbegrenzung](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) für PHP in Ihrer Umgebung in `php.ini`.

Alternativ können Sie die Speicherbegrenzung mit diesem Befehl angeben: `php -d memory_limit=-1 [path to composer]/composer require magento/quick-checkout`.

Beispiel:

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/quick-checkout
```

## Hinzufügen von Adresszeilen mit neuer Lieferadresse

Es gibt ein bekanntes Problem für die Quick Checkout-Erweiterung.

Wenn Sie [mit einem Bolt-Konto anmelden](https://help.bolt.com/shoppers/guides/checkout/log-in/)können Sie eine neue Versandadresse mit einer Begrenzung von 4 Zeilen pro Straßenadresse hinzufügen.

Wenn die neue Lieferadresse mehr als 4 Zeilen enthält, werden diese nicht gespeichert.

Adobe Commerce kann in der Regel so konfiguriert werden, dass bis zu 20 Adresszeilen unterstützt werden.

## Unerwartetes Verhalten bei `Display Billing Address On` auf `payment page`

Es gibt ein bekanntes Problem für die Quick Checkout-Erweiterung.

Wenn Sie die `Display Billing Address On` -Parameter auf `payment page` und [mit einem Bolt-Konto anmelden](https://help.bolt.com/shoppers/guides/checkout/log-in/) Wenn Sie die `My billing and shipping address are the same` Kontrollkästchen aktivieren, wird das Optionsfeld angezeigt `use existing card`. Da die Rechnungsadresse nur für neue Kreditkarten gilt, ist die Adresse erst sichtbar, wenn der Bolt-Benutzer sich entscheidet, eine neue Kreditkartenoption hinzuzufügen.

Siehe [Checkout](https://docs.magento.com/user-guide/configuration/sales/checkout.html) für weitere Informationen zum Thema `Display Billing Address On` -Parameter.
