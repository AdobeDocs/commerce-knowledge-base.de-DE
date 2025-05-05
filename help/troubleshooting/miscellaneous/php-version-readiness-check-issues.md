---
title: Probleme bei der Prüfung der PHP-Version
description: Dieser Artikel beschreibt die Lösungen für die PHP-Versionsprobleme, die bei der lokalen Installation/Aktualisierung von Adobe Commerce mithilfe des Websetup-Assistenten auftreten können.
exl-id: dee939cf-b9b2-4750-965c-5b8908a4498d
feature: Variables
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# Probleme bei der Prüfung der PHP-Version

Dieser Artikel beschreibt die Lösungen für die PHP-Versionsprobleme, die bei der lokalen Installation/Aktualisierung von Adobe Commerce mithilfe des Websetup-Assistenten auftreten können.

>[!WARNING]
>
>Beachten Sie bei Adobe Commerce in der Cloud-Infrastruktur, dass Service-Upgrades nicht ohne eine Vorankündigung von 48 Geschäftsstunden an unser Infrastrukturteam in die Produktionsumgebung übertragen werden können. Dies ist erforderlich, da wir sicherstellen müssen, dass wir einen Support-Techniker für die Infrastruktur zur Verfügung haben, der Ihre Konfiguration innerhalb eines gewünschten Zeitraums mit minimalen Ausfallzeiten in Ihrer Produktionsumgebung aktualisiert. 48 Stunden vor dem Zeitpunkt, zu dem Ihre Änderungen in der Produktion vorgenommen werden müssen ([ ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)), wobei das erforderliche Service-Upgrade detailliert angegeben und der Zeitpunkt angegeben wird, zu dem das Upgrade gestartet werden soll.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Nicht unterstützte PHP-Version

### Problem

Die Prüfung schlägt fehl, weil Sie eine nicht unterstützte PHP-Version verwenden.

### Lösung

Um dieses Problem zu beheben, verwenden Sie eine der unterstützten Versionen, die in unserer Entwicklerdokumentation [2.3.x Systemanforderungen](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/system-requirements) und [2.2.x Systemanforderungen](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/system-requirements) aufgeführt sind.

## PHP Readiness Check wird nicht angezeigt

### Problem

Die PHP Readiness Check zeigt die PHP-Version nicht wie in der folgenden Abbildung dargestellt an.
![upgr-tshooting-no-cron.png](assets/upgr-tshoot-no-cron.png)

### Lösung

Dies ist ein Symptom für ein falsches Cron-Auftragssetup. Weitere Informationen finden Sie unter [Einrichten von Cron-Aufträgen](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/next-steps/configuration) in unserer Entwicklerdokumentation.

## Falsche PHP-Version

### Problem

Die Prüfung meldet die falsche PHP-Version. Normalerweise geschieht dies nur bei fortgeschrittenen Benutzern, die mehrere PHP-Versionen installiert haben. In einigen Fällen schlägt die Bereitschaftsprüfung fehl; in anderen Fällen kann sie erfolgreich sein.

Wenn die von der Readiness Check gemeldete PHP-Version falsch ist, ist dies das Ergebnis einer Diskrepanz der PHP-Versionen zwischen der PHP-CLI und dem Webserver-Plug-in. Adobe Commerce verlangt, dass Sie *eine Version* von PHP sowohl für die CLI (auf der cron ausgeführt wird) als auch für den Webserver (auf dem Commerce Admin, der Komponenten-Manager und das System-Upgrade ausgeführt werden) verwenden.

### Lösung

Wir gehen davon aus, dass Sie, wenn Sie dieses Problem haben, ein fortgeschrittener Benutzer sind, der wahrscheinlich mehrere Versionen von PHP auf Ihrem System installiert hat.

Um das Problem zu beheben, versuchen Sie Folgendes:

* Starten Sie Ihren Webserver oder php-fm neu.
* Überprüfen Sie die `$PATH` Umgebungsvariable auf mehrere Pfade zu PHP.
* Verwenden Sie den `which php` Befehl, um die erste ausführbare PHP-Datei in Ihrem Pfad zu finden; wenn sie nicht korrekt ist, entfernen Sie sie oder erstellen Sie einen Symlink zur richtigen PHP-Version.
* Verwenden Sie eine [`phpinfo.php`](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/prerequisites/optional-software) Seite, um weitere Informationen zu erfassen.
* Stellen Sie sicher, dass Sie eine unterstützte PHP-Version gemäß unseren Systemanforderungen ausführen, in unserer Entwicklerdokumentation:
   * [Adobe Commerce-Systemanforderungen](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/system-requirements)
* Stellen Sie die gleichen PHP-Einstellungen für die PHP-Befehlszeile und das PHP-Webserver-Plug-in ein, wie in [PHP-Konfigurationsoptionen](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/system-requirements#php-settings) in unserer Entwicklerdokumentation beschrieben.
