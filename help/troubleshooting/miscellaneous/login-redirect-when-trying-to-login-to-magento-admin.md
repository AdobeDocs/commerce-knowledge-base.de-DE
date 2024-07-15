---
title: Login-Umleitung bei der Anmeldung bei Commerce Admin
description: In diesem Artikel finden Sie die möglichen Lösungen für das Commerce Admin-Anmeldeproblem, bei dem Sie beim Versuch, sich beim Administrator anzumelden, zum Anmeldeformular zurückgeleitet werden und keine Fehlermeldung angezeigt wird. Dazu gehören das Korrigieren der Zeitzoneneinstellungen des Servers und das Löschen der Cookie-Einstellungen in Adobe Commerce.
exl-id: ff3114fd-8690-4983-8221-cf807f083b15
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# Login-Umleitung bei der Anmeldung bei Commerce Admin

In diesem Artikel finden Sie die möglichen Lösungen für das Commerce Admin-Anmeldeproblem, bei dem Sie beim Versuch, sich beim Administrator anzumelden, zum Anmeldeformular zurückgeleitet werden und keine Fehlermeldung angezeigt wird. Dazu gehören das Korrigieren der Zeitzoneneinstellungen des Servers und das Löschen der Cookie-Einstellungen in Adobe Commerce.

## Betroffene Versionen:

Alle Adobe Commerce-Versionen und -Editionen.

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Rufen Sie Ihre Commerce-Admin-Seite auf.
1. Geben Sie Ihre Anmeldedaten ein und klicken Sie auf Anmelden.

<u>Erwartete Ergebnisse</u>:

Sie werden beim Commerce-Administrator angemeldet.

<u>Tatsächliche Ergebnisse</u>:

Sie werden ohne Fehlermeldungen zum Anmeldeformular zurückgeleitet.

## Ursache

Es gibt mehrere mögliche Gründe für das Problem:

* Falsche Zeitzone auf Browserebene (was dazu führt, dass die Admin-Sitzung als abgelaufen gilt, selbst wenn ihre tatsächliche Lebensdauer noch nicht abgelaufen ist).
* Falsche Cookie-Einstellungen, was dazu führt, dass die festgelegte Sitzung von Adobe Commerce nicht verwendet wird.

In den nächsten Absätzen finden Sie Lösungen für jeden Fall.

## Lösungen

### Problem bei der Lebensdauer der Admin-Sitzung

Versuchen Sie, einen anderen Browser zu verwenden und die Lebensdauer der Admin-Sitzung zu erhöhen, wenn sie weniger als eine Stunde beträgt.

Gehen Sie wie folgt vor, um die Lebensdauer der Admin-Sitzung zu erhöhen:

1. Erstellen Sie eine Datenbanksicherung.
1. Verwenden Sie ein Datenbank-Tool wie [phpMyAdmin](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/optional.html#install-optional-phpmyadmin) oder greifen Sie über die Befehlszeile manuell auf die DB zu, um die folgende SQL-Abfrage auszuführen:

   ```sql
   UPDATE core_config_data SET value = 7200 WHERE path = 'admin/security/session_lifetime';
   ```

1. Bereinigen Sie den Konfigurationscache, indem Sie den folgenden Befehl ausführen:

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```

### Falsche Cookie-Einstellungen

Gehen Sie wie folgt vor, um die Werte der Cookie-Einstellungen zu überprüfen und zu löschen:

1. Erstellen Sie eine Datenbanksicherung.
1. Verwenden Sie ein Datenbank-Tool wie [phpMyAdmin](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/optional.html#install-optional-phpmyadmin) oder greifen Sie über die Befehlszeile manuell auf die DB zu, um die folgende SQL-Abfrage auszuführen:

   ```sql
   SELECT * FROM core_config_data WHERE (path = "web/cookie/cookie_domain" OR path = "web/cookie/cookie_path");
   ```

1. Wenn die Antworten der Werte nicht leer sind, setzen Sie sie durch Ausführen auf NULL:

   ```sql
   UPDATE core_config_data SET value = NULL WHERE (path = "web/cookie/cookie_domain" OR path = "web/cookie/cookie_path");
   ```

1. Bereinigen Sie den Konfigurationscache, indem Sie den folgenden Befehl ausführen:

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```

## Verwandte Artikel

* [Kehren Sie zum Formular für die Admin-Anmeldung mit dem Fehler &quot;Ihr Konto ist vorübergehend deaktiviert&quot;zurück](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error.md) in unserer Support-Wissensdatenbank.
* [Kehren Sie zum Formular für die Admin-Anmeldung mit dem Fehler &quot;Ihre aktuelle Sitzung ist abgelaufen&quot;zurück](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-current-session-has-been-expired-error.md) in unserer Support-Wissensdatenbank.
