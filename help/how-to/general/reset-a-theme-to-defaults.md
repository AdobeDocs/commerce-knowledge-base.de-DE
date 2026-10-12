---
title: Reset a theme to defaults
description: Abhängig von Problemen, auf die Sie beim Anpassen Ihrer Designs und Entwickeln Ihres Stores stoßen können, haben Sie möglicherweise keinen Zugriff über den Commerce-Administrator. Sie können das Design löschen und auf die Standardeinstellung zurücksetzen, ohne auf den Administrator zugreifen zu müssen. Nachdem Sie das Design gelöscht haben, wird das Standard-Luma-Design angewendet.
exl-id: 86304dd5-f448-4dcc-ad07-04ecc6c85b6d
feature: Cache
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%
---
# Reset a theme to defaults

Abhängig von Problemen, auf die Sie beim Anpassen Ihrer Designs und Entwickeln Ihres Stores stoßen können, haben Sie möglicherweise keinen Zugriff über den Commerce-Administrator. Sie können das Design löschen und auf die Standardeinstellung zurücksetzen, ohne auf den Administrator zugreifen zu müssen. Nachdem Sie das Design gelöscht haben, wird das Standard-Luma-Design angewendet.

Während Sie Adobe Commerce (alle Bereitstellungen) und Magento Open Source-Komponenten (Module, Designs und Sprachpakete) entwickeln, müssen Sie in Ihrer sich schnell verändernden Umgebung regelmäßig bestimmte Ordner und Caches löschen. Andernfalls wird der Code mit Ausnahmen ausgeführt und funktioniert nicht ordnungsgemäß. Weitere Informationen finden Sie unter [Löschen von Ordnern während der Entwicklung](https://developer.adobe.com/commerce/php/development/components/clear-directories/) in unserer Entwicklerdokumentation.

## Umwelt und Technologien

* Adobe Commerce On-Premises
* Adobe Commerce auf Cloud-Infrastruktur
* Magento Open Source

## Voraussetzungen

* Datenbank-Tools

## Schritte

Wenn Sie das Store-Design zurücksetzen müssen, aber nicht auf das Admin-Bedienfeld zugreifen können, können Sie es wie folgt in der Datenbank zurücksetzen:

1. Verwenden Sie ein Datenbank-Tool wie [phpMyAdmin](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin) oder greifen Sie manuell über die Befehlszeile auf die DB zu, um die folgende SQL-Abfrage auszuführen: `UPDATE core_config_data SET value=NULL WHERE path='design/theme/theme_id'`
1. Löschen Sie die folgenden Ordner:
   * `pub/static/frontend`
   * `var/view_preprocessing`
   * `var/cache`
   * `var/page_cache`

Auf diese Weise wird kein Design auf der Store-Ansichtsebene festgelegt und wenn Sie die Store-Frontseiten neu laden, wird das Standard-Luma-Design angewendet.

## Zusätzliche Informationen

* [Ordner während der Entwicklung löschen](https://developer.adobe.com/commerce/php/development/components/clear-directories/) in unserer Entwicklerdokumentation
