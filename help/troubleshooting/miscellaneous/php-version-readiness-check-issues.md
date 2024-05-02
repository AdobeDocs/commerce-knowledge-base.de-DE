---
title: Probleme bei der Überprüfung der PHP-Versionsbereitschaft
description: In diesem Artikel werden die Lösungen für die Probleme der PHP-Version beschrieben, die bei der Installation/Aktualisierung von Adobe Commerce vor Ort mit dem Web-Setup-Assistenten auftreten können.
exl-id: dee939cf-b9b2-4750-965c-5b8908a4498d
feature: Variables
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# Probleme bei der Überprüfung der PHP-Versionsbereitschaft

In diesem Artikel werden die Lösungen für die Probleme der PHP-Version beschrieben, die bei der Installation/Aktualisierung von Adobe Commerce vor Ort mit dem Web-Setup-Assistenten auftreten können.

>[!WARNING]
>
>Beachten Sie bei Adobe Commerce zur Cloud-Infrastruktur, dass Service-Upgrades nicht ohne 48-Stunden-Benachrichtigung an unser Infrastrukturteam in die Produktionsumgebung gesendet werden können. Dies ist erforderlich, da wir sicherstellen müssen, dass wir über einen Infrastruktur-Support-Mitarbeiter verfügen, der Ihre Konfiguration innerhalb eines gewünschten Zeitraums mit minimalen Ausfallzeiten in Ihrer Produktionsumgebung aktualisiert. 48 Stunden vor dem Zeitpunkt, zu dem Ihre Änderungen in der Produktion sein müssen [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) Geben Sie die erforderliche Dienstaktualisierung an und geben Sie den Zeitpunkt an, zu dem die Aktualisierung beginnen soll.

## Betroffene Produkte und Versionen

* Adobe Commerce lokal 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Nicht unterstützte PHP-Version

### Problem

Die Prüfung schlägt fehl, da Sie eine nicht unterstützte PHP-Version verwenden.

### Lösung

Um dieses Problem zu beheben, verwenden Sie eine der unterstützten Versionen, die in unserer Entwicklerdokumentation aufgeführt sind [2.3.x Systemanforderungen](https://devdocs.magento.com/guides/v2.3/install-gde/system-requirements.html) und [2.2.x Systemanforderungen](https://devdocs.magento.com/guides/v2.2/install-gde/system-requirements.html).

## Die PHP-Kompatibilitätsprüfung wird nicht angezeigt

### Problem

Die PHP Ready Check zeigt die PHP-Version nicht wie in der folgenden Abbildung dargestellt.
![upgr-tshooting-no-cron.png](assets/upgr-tshoot-no-cron.png)

### Lösung

Dies ist ein Symptom der falschen Einrichtung von Cron-Aufträgen. Weitere Informationen finden Sie unter [Einrichten von Cron-Aufträgen](https://devdocs.magento.com/guides/v2.3/install-gde/install/post-install-config.html#post-install-cron) in unserer Entwicklerdokumentation.

## Falsche PHP-Version

### Problem

Die Prüfung meldet die falsche PHP-Version. Normalerweise geschieht dies nur für fortgeschrittene Benutzer, die mehrere PHP-Versionen installiert haben. In einigen Fällen schlägt die Bereitschaftsprüfung fehl, in anderen Fällen sogar.

Wenn die PHP-Version, die von der Readiness-Prüfung gemeldet wurde, falsch ist, ist dies das Ergebnis einer Inkongruenz der PHP-Versionen zwischen der PHP-CLI und dem Webserver-Plug-in. Adobe Commerce erfordert die Verwendung von *eine Version* von PHP sowohl für die CLI (auf der Cron ausgeführt wird) als auch für den Webserver (auf dem Commerce Admin, Component Manager und System Upgrade ausgeführt werden).

### Lösung

Wir gehen davon aus, dass Sie, wenn Sie dieses Problem haben, ein fortgeschrittener Benutzer sind, der wahrscheinlich mehrere Versionen von PHP auf Ihrem System installiert hat.

Um das Problem zu beheben, versuchen Sie Folgendes:

* Starten Sie Ihren Webserver oder php-fm neu.
* Überprüfen Sie die `$PATH` Umgebungsvariable für mehrere Pfade zu PHP.
* Verwenden Sie die `which php` -Befehl, um die erste ausführbare PHP-Datei in Ihrem Pfad zu finden; wenn sie nicht korrekt ist, entfernen Sie sie oder erstellen Sie einen Symlink zur richtigen PHP-Version.
* Verwenden Sie eine [`phpinfo.php`](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/optional.html#install-optional-phpinfo) , um weitere Informationen zu sammeln.
* Stellen Sie sicher, dass Sie eine unterstützte PHP-Version gemäß unseren Systemanforderungen in unserer Entwicklerdokumentation ausführen:
   * [Systemanforderungen für Adobe Commerce 2.3.x](https://devdocs.magento.com/guides/v2.3/install-gde/system-requirements.html)
   * [Systemanforderungen für Adobe Commerce 2.2.x](https://devdocs.magento.com/guides/v2.2/install-gde/system-requirements.html)
* Legen Sie dieselben PHP-Einstellungen für die PHP-Befehlszeile und das PHP-Webserver-Plug-in fest, wie im Abschnitt [PHP-Konfigurationsoptionen](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-centos-ubuntu.html) in unserer Entwicklerdokumentation.
