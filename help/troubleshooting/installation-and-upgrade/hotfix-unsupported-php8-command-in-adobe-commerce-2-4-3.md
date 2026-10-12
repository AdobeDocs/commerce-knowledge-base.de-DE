---
title: Adobe Commerce Upgrade 2.4.3, 2.3.7-p1 PHP Schwerwiegender Fehler Hotfix
description: 'Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass Händler versuchen, auf Adobe Commerce (alle Bereitstellungsmethoden) oder Magento Open Source 2.4.3 oder 2.3.7-p1 zu aktualisieren, der folgende Fehler angezeigt wird:'
exl-id: 1c472214-8387-403e-b2d2-d3f3c9e1da6a
feature: Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%
---
# Adobe Commerce Upgrade 2.4.3, 2.3.7-p1 PHP Schwerwiegender Fehler Hotfix

Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass Händler versuchen, auf Adobe Commerce (alle Bereitstellungsmethoden) oder Magento Open Source 2.4.3 oder 2.3.7-p1 zu aktualisieren, der folgende Fehler angezeigt wird:

*Schwerwiegender PHP-Fehler: Nicht abgefangener Fehler: Aufruf der undefinierten Funktion Magento\Framework\Filesystem\Directory\str_contains() in &lt;…>/magento/vendor/magento/framework/Filesystem/Directory/DenyListPathValidator.php:74*

Das Problem wird im Umfang der Versionen 2.4.4, 2.4.3-p1 und 2.3.7-p2 behoben.

## Betroffene Versionen und Produkte

* Adobe Commerce (alle Bereitstellungsmethoden) beim Upgrade auf 2.3.7-p1 oder 2.4.3.
* Magento Open Source beim Upgrade auf 2.3.7-p1 oder 2.4.3.

## Problem

Das Problem wird durch die neuen Adobe Commerce-Versionen 2.4.3 und 2.3.7-p1 verursacht, die nur PHP 8-`str_contains` verwenden. Adobe Commerce 2.4.3 und 2.3.7-p1 sind nur mit PHP 7.4 kompatibel, sodass diese Funktion nicht verwendet werden kann.

<u>Schritte zur Reproduktion</u> :

Versuchen Sie, auf Adobe Commerce 2.4.3 oder 2.3.7-p1 zu aktualisieren.

<u>Erwartetes Ergebnis:</u>

Erfolgreiches Upgrade.

<u>Tatsächliches Ergebnis:</u>

Schwerwiegender PHP-Fehler.

## Lösung

Als Problemumgehung führen Sie den folgenden Befehl in der CLI/Terminal-Konsole aus: `composer require symfony/polyfill-php80` aus dem Magento-Stammordner oder installieren Sie einen Composer-Patch.

Um das Problem für 2.4.3 zu beheben, sollten Adobe Commerce (alle Bereitstellungsmethoden) und Magento Open Source-Händler einen Patch anwenden:

[AC-384_Fix_Incompatible_PHP_Method__2.4.3_ce.patch](assets/AC-384__Fix_Incompatible_PHP_Method__2.4.3_ce.patch.zip)

Um das Problem für 2.3.7-p1 zu beheben, sollten Adobe Commerce (alle Bereitstellungsmethoden) und Magento Open Source-Händler den Patch anwenden:

[AC-384__FIX_INCOMPATIBLE_PHP_METHOD__2.3.7-p1_ce.patch](assets/AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch.zip)

## Anwenden des Patches

Anweisungen finden [&#x200B; unter „Anwenden eines von Magento bereitgestellten Composer](https://experienceleague.adobe.com/de/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/how-to-apply-a-composer-patch-provided-by-magento)Patches .

## Verwandtes Lesen

GitHub [Nicht unterstützter PHP 8-Befehl in Magento 2.4.3 EE #33680](https://github.com/magento/magento2/issues/33680)
