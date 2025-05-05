---
title: PHP-Versionsfehler oder 404-Fehler beim Zugriff auf Adobe Commerce im Browser
description: Dieser Artikel bietet Lösungen für die Fälle, in denen Sie in einem Webbrowser nicht auf Ihre Adobe Commerce-Instanz zugreifen können und der Fehler „404 error“ oder „Unsupported PHP version“ (Nicht unterstützte PHP-Version) ausgegeben wird.
exl-id: 6cfdeaae-5e52-411c-9006-5af8a467873a
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# PHP-Versionsfehler oder 404-Fehler beim Zugriff auf Adobe Commerce im Browser

Dieser Artikel bietet Lösungen für die Fälle, in denen Sie in einem Webbrowser nicht auf Ihre Adobe Commerce-Instanz zugreifen können und der Fehler „404 error“ oder „Unsupported PHP version“ (Nicht unterstützte PHP-Version) ausgegeben wird.

## Betroffene Produkte und Versionen:

* Adobe Commerce 2.3.x

## Problem: Nicht unterstützte PHP-Version

Die folgende Meldung wird angezeigt, wenn Sie versuchen, auf die Adobe Commerce-Storefront oder Commerce Admin zuzugreifen:

`Magento supports PHP 7.1.3 or later. Please read Magento System Requirements.`

### Lösung

Probieren Sie Folgendes aus:

* Aktualisieren Sie PHP auf Version 7.3. Weitere Informationen finden Sie unter [Anforderungen für den Technologie-Stack von Adobe Commerce 2.3](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/system-requirements) in unserer Entwicklerdokumentation.
* Starten Sie Apache neu, da es möglicherweise nicht dieselbe PHP-Version verwendet wie im Dateisystem. Um Apache neu zu starten, verwenden Sie die folgenden Befehle:
   * Ubuntu: `service apache2 restart`
   * CentOS: `service httpd restart`

## Problem: Fehler 404

Beim Versuch, auf die Adobe Commerce-Storefront oder Commerce Admin zuzugreifen, wird der Fehler 404 (Nicht gefunden) angezeigt.

### Lösung

Probieren Sie Folgendes aus:

* Stellen Sie sicher[ dass „Apache](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/prerequisites/web-server/apache)Server-Neuschreibungen“ aktiviert sind. Wenn Apache-Server-Neuschreibungen falsch eingestellt sind, werden statische Dateien nicht vom richtigen Speicherort bereitgestellt.
* Es kann ein Problem mit der während der Installation eingegebenen Basis-URL auftreten. Sie geben die Basis-URL als Wert von `--base-url=` bei der Installation von Adobe Commerce über die Befehlszeile oder als Wert des Felds **Ihre Store-**&quot; auf der Seite Web-Konfiguration des Web-Installationsprogramms an. Die Basis-URL *muss* mit dem Schema beginnen (z. B. `http://` ) und mit einem Schrägstrich (/) enden. Führen Sie das Installationsprogramm erneut mit einem gültigen Wert aus und versuchen Sie anschließend, auf Adobe Commerce zuzugreifen.
