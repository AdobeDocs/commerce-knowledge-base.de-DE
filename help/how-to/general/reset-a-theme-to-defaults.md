---
title: Zurücksetzen eines Designs auf die Standardeinstellungen
description: Je nach Problemen, die bei der Anpassung Ihrer Designs und der Entwicklung Ihres Stores auftreten können, haben Sie möglicherweise keinen Zugriff über den Commerce-Administrator. Sie können Ihren Designstandard löschen und zurücksetzen, ohne auf den Administrator zugreifen zu müssen. Nachdem Sie das Design gelöscht haben, wird das standardmäßige Luma-Design angewendet.
exl-id: 86304dd5-f448-4dcc-ad07-04ecc6c85b6d
feature: Cache
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Zurücksetzen eines Designs auf die Standardeinstellungen

Je nach Problemen, die bei der Anpassung Ihrer Designs und der Entwicklung Ihres Stores auftreten können, haben Sie möglicherweise keinen Zugriff über den Commerce-Administrator. Sie können Ihren Designstandard löschen und zurücksetzen, ohne auf den Administrator zugreifen zu müssen. Nachdem Sie das Design gelöscht haben, wird das standardmäßige Luma-Design angewendet.

Während Sie Adobe Commerce (alle Implementierungen) und Magento Open Source-Komponenten (Module, Designs und Sprachpakete) entwickeln, müssen Sie in Ihrer sich rasch wandelnden Umgebung regelmäßig bestimmte Ordner und Caches löschen. Andernfalls wird Ihr Code mit Ausnahmen ausgeführt und funktioniert nicht ordnungsgemäß. Weitere Informationen finden Sie unter [Löschen von Ordnern während der Entwicklung](https://devdocs.magento.com/guides/v2.2/howdoi/php/php_clear-dirs.html) in unserer Entwicklerdokumentation.

## Umwelt und Technologien

* Adobe Commerce vor Ort
* Adobe Commerce auf Cloud-Infrastruktur
* Magento Open Source

## Voraussetzungen

* Datenbankwerkzeuge

## Schritte

Wenn Sie das Store-Design zurücksetzen müssen, aber nicht auf das Admin-Bedienfeld zugreifen können, können Sie es in der Datenbank zurücksetzen, indem Sie Folgendes durchführen:

1. Verwenden Sie ein Datenbank-Tool wie [phpMyAdmin](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/optional.html#install-optional-phpmyadmin) oder greifen Sie über die Befehlszeile manuell auf die DB zu, um die folgende SQL-Abfrage auszuführen: `UPDATE core_config_data SET value=NULL WHERE path='design/theme/theme_id'`
1. Löschen Sie die folgenden Ordner:
   * `pub/static/frontend`
   * `var/view_preprocessing`
   * `var/cache`
   * `var/page_cache`

Auf diese Weise wird kein Design auf der Store-Ansichtsebene festgelegt. Wenn Sie die Storefront-Seiten neu laden, wird das standardmäßige Luma-Design angewendet.

## Zusätzliche Informationen

* [Löschen von Verzeichnissen während der Entwicklung](https://devdocs.magento.com/guides/v2.2/howdoi/php/php_clear-dirs.html) in unserer Entwicklerdokumentation
