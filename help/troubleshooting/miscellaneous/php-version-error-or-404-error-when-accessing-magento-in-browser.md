---
title: PHP-Versionsfehler oder 404-Fehler beim Zugriff auf Adobe Commerce im Browser
description: Dieser Artikel bietet Lösungen für Probleme, bei denen Sie nicht in einem Webbrowser auf Ihre Adobe Commerce-Instanz zugreifen können und einen 404-Fehler oder Fehler "Nicht unterstützte PHP-Version"erhalten.
exl-id: 6cfdeaae-5e52-411c-9006-5af8a467873a
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# PHP-Versionsfehler oder 404-Fehler beim Zugriff auf Adobe Commerce im Browser

Dieser Artikel bietet Lösungen für Probleme, bei denen Sie nicht in einem Webbrowser auf Ihre Adobe Commerce-Instanz zugreifen können und einen 404-Fehler oder Fehler &quot;Nicht unterstützte PHP-Version&quot;erhalten.

## Betroffene Produkte und Versionen:

* Adobe Commerce 2.3.x

## Problem: Nicht unterstützte PHP-Version

Die folgende Meldung wird angezeigt, wenn Sie versuchen, auf die Adobe Commerce Storefront oder Commerce Admin zuzugreifen:

`Magento supports PHP 7.1.3 or later. Please read Magento System Requirements.`

### Lösung

Versuchen Sie Folgendes:

* Aktualisieren Sie PHP auf Version 7.3. Weitere Informationen finden Sie unter [Stapelanforderungen für die Adobe Commerce 2.3-Technologie](https://devdocs.magento.com/guides/v2.3/install-gde/system-requirements.html#php) in unserer Entwicklerdokumentation.
* Starten Sie Apache neu, da es möglicherweise nicht dieselbe PHP-Version wie im Dateisystem verwendet. Verwenden Sie die folgenden Befehle, um Apache neu zu starten:
   * Ubuntu: `service apache2 restart`
   * CentOS: `service httpd restart`

## Problem: Fehler 404

Beim Zugriff auf die Adobe Commerce Storefront oder Commerce Admin wird der Fehler 404 (Nicht gefunden) angezeigt.

### Lösung

Versuchen Sie Folgendes:

* Stellen Sie sicher [Neuschreibungen des Apache-Servers](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/apache.html) aktiviert sind. Wenn die Neuschreibungen des Apache-Servers falsch eingestellt sind, werden statische Dateien nicht vom richtigen Speicherort bereitgestellt.
* Es kann ein Problem mit der Basis-URL geben, die Sie während der Installation eingegeben haben. Sie geben die Basis-URL als Wert von `--base-url=` bei der Installation von Adobe Commerce über die Befehlszeile oder als Wert des **Ihre Store-Adresse** auf der Web-Konfigurationsseite des Webinstallationsprogramms. Die Basis-URL *must* Beginn mit dem System (z. B. `http://` ) und mit einem Schrägstrich (/) enden. Führen Sie das Installationsprogramm erneut mit einem gültigen Wert aus und versuchen Sie danach, auf Adobe Commerce zuzugreifen.
