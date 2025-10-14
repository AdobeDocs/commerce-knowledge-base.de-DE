---
title: Adobe Commerce Upgrade 2.4.3, 2.3.7-p1 PHP Schwerwiegender Fehler Hotfix
description: 'Dieser Artikel bietet eine Fehlerbehebung für Händler, die versuchen, auf Adobe Commerce (alle Bereitstellungsmethoden) oder Magento Open Source 2.4.3 oder 2.3.7-p1 zu aktualisieren, wenn der folgende Fehler angezeigt wird:'
exl-id: 1c472214-8387-403e-b2d2-d3f3c9e1da6a
feature: Install, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Adobe Commerce Upgrade 2.4.3, 2.3.7-p1 PHP Schwerwiegender Fehler Hotfix

Dieser Artikel bietet eine Fehlerbehebung für Händler, die versuchen, auf Adobe Commerce (alle Bereitstellungsmethoden) oder Magento Open Source 2.4.3 oder 2.3.7-p1 zu aktualisieren, wenn der folgende Fehler angezeigt wird:

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

Anweisungen [&#x200B; Sie unter „Anwenden eines Composer-Patches von Magento](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

## Verwandtes Lesen

GitHub [Nicht unterstützter PHP 8-Befehl in Magento 2.4.3 EE #33680](https://github.com/magento/magento2/issues/33680)
