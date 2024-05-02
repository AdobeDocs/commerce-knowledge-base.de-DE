---
title: Gehen Sie zurück zum Anmeldeformular für die Commerce Admin mit dem Fehler "Ihre aktuelle Sitzung ist abgelaufen".
description: '"Dieser Artikel enthält die möglichen Lösungen für das Commerce Admin-Anmeldeproblem, bei dem Sie mit der folgenden Fehlermeldung zum Anmeldeformular zurückgeleitet werden: *"Ihre aktuelle Sitzung ist abgelaufen"*. Zu den Lösungen gehören die Überprüfung auf Probleme bei der Serverzeiteinstellung und die Änderung der Einstellungen für die Sitzungsspeicherung."'
exl-id: 29df2ed2-ff4a-4f1a-bdb7-1160416cda00
feature: Admin Workspace
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# Gehen Sie zurück zum Anmeldeformular für die Commerce Admin mit dem Fehler &quot;Ihre aktuelle Sitzung ist abgelaufen&quot;.

In diesem Artikel finden Sie die möglichen Lösungen für das Commerce Admin-Anmeldeproblem, bei dem Sie mit der folgenden Fehlermeldung zurück zum Anmeldeformular weitergeleitet werden: *&quot;Ihre aktuelle Sitzung ist abgelaufen&quot;*. Zu den Lösungen gehören die Überprüfung auf Probleme bei der Serverzeiteinstellung und die Änderung der Einstellungen für die Sitzungsspeicherung.

## Betroffene Versionen:

Alle Adobe Commerce-Versionen und -Editionen

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Rufen Sie die Commerce-Admin-Seite auf.
1. Geben Sie Ihre Anmeldedaten ein und klicken Sie auf Anmelden.

<u>Erwartetes Ergebnis</u>:

Sie werden beim Commerce-Administrator angemeldet.

<u>Tatsächliches Ergebnis</u>:

Sie werden zum Anmeldeformular zurückgeleitet, wobei die folgende Fehlermeldung angezeigt wird: *&quot;Ihre aktuelle Sitzung ist abgelaufen&quot;*.

## Ursache

Es kann zwei mögliche Gründe für das Problem geben:

* Problem mit Serverzeiteinstellungen
* Problem mit Sitzungsspeicherung

Im folgenden Abschnitt finden Sie Lösungen.

## Lösung

### Probleme mit den Serverzeiteinstellungen prüfen

Überprüfen Sie den Sitzungsdatensatz, der im `admin_user_session` Tabelle. Wenn die Werte von `created_at` und/oder `updated_at` falsch sind, kann dies durch das Problem mit Serverzeiteinstellungen verursacht werden. Bitten Sie Ihren Serversystemadministrator, dies zu überprüfen. Beachten Sie, dass die Uhrzeit in DB standardmäßig auf UTC festgelegt ist.

### Sitzungsspeicher ändern

Versuchen Sie, den Sitzungsspeicher zu ändern. Verwenden Sie die Informationen aus dem [Sitzungsdateien finden](https://devdocs.magento.com/guides/v2.3/config-guide/sessions.html) in unserer Entwicklerdokumentation , um herauszufinden, wo Ihre Sitzung gespeichert ist, und es zu ändern, indem Sie die `app/etc/env.php` -Datei.

Um beispielsweise die Sitzung im Dateisystem zu speichern, ändern Sie die `'session'` wie folgt:

```php
....
'session' =>
    array (
      'save' => 'files',
),
....
```

Führen Sie die `bin/magento app:config:import` -Befehl zum Importieren von Konfigurationsdaten.


## Verwandtes Lesen

* [Daten aus Konfigurationsdateien importieren](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-config-mgmt-import.html) in unserer Entwicklerdokumentation
* [Konfigurieren von Redis](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html) in unserer Entwicklerdokumentation
* [Gehen Sie zurück zum Anmeldeformular für die Commerce Admin mit dem Fehler &quot;Ihr Konto ist vorübergehend deaktiviert&quot;.](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error.md) in unserer Wissensdatenbank
* [Kehren Sie beim Versuch, sich beim Commerce-Administrator anzumelden, ohne Fehler zum Anmeldeformular zurück.](/help/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin.md) in unserer Wissensdatenbank
