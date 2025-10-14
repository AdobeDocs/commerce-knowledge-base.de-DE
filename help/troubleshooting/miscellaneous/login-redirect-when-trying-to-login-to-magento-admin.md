---
title: Anmeldeumleitung bei Anmeldung bei Commerce Admin
description: In diesem Artikel finden Sie die möglichen Lösungen für das Commerce Admin-Anmeldeproblem, bei dem Sie beim Anmeldeversuch bei Admin zurück zum Anmeldeformular weitergeleitet werden und keine Fehlermeldung angezeigt wird. Dazu gehören die Korrektur der Zeitzoneneinstellungen des Servers und das Löschen der Cookie-Einstellungen in Adobe Commerce.
exl-id: ff3114fd-8690-4983-8221-cf807f083b15
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# Anmeldeumleitung bei Anmeldung bei Commerce Admin

In diesem Artikel finden Sie die möglichen Lösungen für das Commerce Admin-Anmeldeproblem, bei dem Sie beim Anmeldeversuch bei Admin zurück zum Anmeldeformular weitergeleitet werden und keine Fehlermeldung angezeigt wird. Dazu gehören die Korrektur der Zeitzoneneinstellungen des Servers und das Löschen der Cookie-Einstellungen in Adobe Commerce.

## Betroffene Editionen und Versionen:

Alle Adobe Commerce-Versionen und -Editionen.

## Problem

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu Ihrer Commerce Admin-Seite.
1. Geben Sie Ihre Anmeldedaten ein und klicken Sie auf Anmelden.

<u>Erwartete Ergebnisse</u>:

Sie werden beim Commerce-Administrator angemeldet.

<u>Tatsächliche Ergebnisse</u>:

Sie werden ohne Fehlermeldungen zurück zum Anmeldeformular weitergeleitet.

## Ursache

Es gibt mehrere mögliche Gründe für das Problem:

* Falsche Zeitzone auf Browser-Ebene festgelegt (was dazu führt, dass die Admin-Sitzung als abgelaufen betrachtet wird, auch wenn ihre tatsächliche Lebensdauer noch nicht abgelaufen ist).
* Falsche Cookie-Einstellungen, was dazu führt, dass die eingerichtete Sitzung von Adobe Commerce nicht verwendet wird.

In den nächsten Absätzen finden Sie jeweils Lösungen.

## Lösungen

### Problem mit der Lebensdauer der Admin-Sitzung

Versuchen Sie, einen anderen Browser zu verwenden und die Lebensdauer der Admin-Sitzung zu verlängern, wenn sie weniger als eine Stunde beträgt.

Um die Lebensdauer der Admin-Sitzung zu verlängern, führen Sie die folgenden Schritte aus:

1. Erstellen Sie eine Datenbanksicherung.
1. Verwenden Sie ein Datenbank-Tool wie [phpMyAdmin](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin) oder greifen Sie manuell über die Befehlszeile auf die Datenbank zu, um die folgende SQL-Abfrage auszuführen:

   ```sql
   UPDATE core_config_data SET value = 7200 WHERE path = 'admin/security/session_lifetime';
   ```

1. Bereinigen Sie den Konfigurations-Cache, indem Sie den folgenden Befehl ausführen:

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```

### Falsche Cookie-Einstellungen

Gehen Sie wie folgt vor, um die Cookie-Einstellungswerte zu überprüfen und zu löschen:

1. Erstellen Sie eine Datenbanksicherung.
1. Verwenden Sie ein Datenbank-Tool wie [phpMyAdmin](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin) oder greifen Sie manuell über die Befehlszeile auf die Datenbank zu, um die folgende SQL-Abfrage auszuführen:

   ```sql
   SELECT * FROM core_config_data WHERE (path = "web/cookie/cookie_domain" OR path = "web/cookie/cookie_path");
   ```

1. Wenn die Antworten der Werte nicht leer sind, legen Sie sie durch Ausführen von auf NULL fest:

   ```sql
   UPDATE core_config_data SET value = NULL WHERE (path = "web/cookie/cookie_domain" OR path = "web/cookie/cookie_path");
   ```

1. Bereinigen Sie den Konfigurations-Cache, indem Sie den folgenden Befehl ausführen:

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```

## Verwandte Artikel

* [Leiten Sie zurück zum Admin-Anmeldeformular mit dem Fehler „Ihr Konto ist vorübergehend deaktiviert“ &#x200B;](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error.md) unserer Support-Wissensdatenbank.
* [Leiten Sie zurück zum Admin-Anmeldeformular mit dem Fehler „Ihre aktuelle Sitzung ist abgelaufen“ &#x200B;](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-current-session-has-been-expired-error.md) unserer Support-Wissensdatenbank.
