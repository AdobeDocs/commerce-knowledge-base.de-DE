---
title: Reset a theme to defaults
description: Abhängig von Problemen, auf die Sie beim Anpassen Ihrer Designs und Entwickeln Ihres Stores stoßen können, haben Sie möglicherweise keinen Zugriff über den Commerce-Administrator. Sie können das Design löschen und auf die Standardeinstellung zurücksetzen, ohne auf den Administrator zugreifen zu müssen. Nachdem Sie das Design gelöscht haben, wird das Standard-Luma-Design angewendet.
exl-id: 86304dd5-f448-4dcc-ad07-04ecc6c85b6d
feature: Cache
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Reset a theme to defaults

Abhängig von Problemen, auf die Sie beim Anpassen Ihrer Designs und Entwickeln Ihres Stores stoßen können, haben Sie möglicherweise keinen Zugriff über den Commerce-Administrator. Sie können das Design löschen und auf die Standardeinstellung zurücksetzen, ohne auf den Administrator zugreifen zu müssen. Nachdem Sie das Design gelöscht haben, wird das Standard-Luma-Design angewendet.

Beim Entwickeln von Adobe Commerce (alle Bereitstellungen) und Ordnerkomponenten (Magento Open Sourcen, Designs und Sprachpakete) müssen Sie aufgrund Ihrer sich schnell verändernden Umgebung bestimmte Ordner und Caches regelmäßig löschen. Andernfalls wird der Code mit Ausnahmen ausgeführt und funktioniert nicht ordnungsgemäß. Weitere Informationen finden Sie unter [Löschen von Ordnern während der Entwicklung](https://developer.adobe.com/commerce/php/development/components/clear-directories/) in unserer Entwicklerdokumentation.

## Umwelt und Technologien

* Adobe Commerce On-Premises
* Adobe Commerce auf Cloud-Infrastruktur
* Magento Open Source

## Voraussetzungen

* Datenbank-Tools

## Schritte

Wenn Sie das Store-Design zurücksetzen müssen, aber nicht auf das Admin-Bedienfeld zugreifen können, können Sie es wie folgt in der Datenbank zurücksetzen:

1. Verwenden Sie ein Datenbank-Tool wie [phpMyAdmin](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin) oder greifen Sie manuell über die Befehlszeile auf die DB zu, um die folgende SQL-Abfrage auszuführen: `UPDATE core_config_data SET value=NULL WHERE path='design/theme/theme_id'`
1. Löschen Sie die folgenden Ordner:
   * `pub/static/frontend`
   * `var/view_preprocessing`
   * `var/cache`
   * `var/page_cache`

Auf diese Weise wird kein Design auf der Store-Ansichtsebene festgelegt und wenn Sie die Store-Frontseiten neu laden, wird das Standard-Luma-Design angewendet.

## Zusätzliche Informationen

* [Ordner während der Entwicklung löschen](https://developer.adobe.com/commerce/php/development/components/clear-directories/) in unserer Entwicklerdokumentation
