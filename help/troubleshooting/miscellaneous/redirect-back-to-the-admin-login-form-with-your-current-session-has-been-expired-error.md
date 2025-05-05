---
title: Leiten Sie mit dem Fehler „Ihre aktuelle Sitzung ist abgelaufen“ zurück zum [!UICONTROL Commerce Admin] Anmeldeformular
description: 'In diesem Artikel finden Sie die möglichen Lösungen für das [!UICONTROL Commerce Admin] Anmeldeproblem, bei dem Sie zurück zum Anmeldeformular mit der folgenden Fehlermeldung geleitet werden: *„Ihre aktuelle Sitzung ist abgelaufen“*. Zu den Lösungen gehören das Überprüfen auf Probleme bei der Server-Zeiteinstellung und das Ändern der Sitzungsspeichereinstellungen.'
exl-id: 29df2ed2-ff4a-4f1a-bdb7-1160416cda00
feature: Admin Workspace
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Leiten Sie mit dem Fehler „Ihre aktuelle Sitzung ist abgelaufen“ zurück zum [!UICONTROL Commerce Admin] Anmeldeformular

In diesem Artikel finden Sie die möglichen Lösungen für das [!UICONTROL Commerce Admin] Anmeldeproblem, bei dem Sie mit der folgenden Fehlermeldung zurück zum Anmeldeformular geleitet werden: *„Ihre aktuelle Sitzung ist abgelaufen“*. Zu den Lösungen gehören das Überprüfen auf Probleme bei der Server-Zeiteinstellung und das Ändern der Sitzungsspeichereinstellungen.

## Betroffene Editionen und Versionen:

Alle Adobe Commerce-Versionen und -Editionen

## Problem

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zur Seite **[!UICONTROL Commerce Admin]** .
1. Geben Sie Ihre Anmeldedaten ein und klicken Sie auf **Anmelden**.

<u>Erwartetes Ergebnis</u>:

Sie werden beim [!UICONTROL Commerce Admin] angemeldet.

<u>Tatsächliches </u>:

Sie werden zurück zum Anmeldeformular weitergeleitet, wobei die folgende Fehlermeldung angezeigt wird: *„Ihre aktuelle Sitzung ist abgelaufen“*.

## Ursache

Es könnte zwei mögliche Gründe für das Problem geben:

* Ein Problem mit den Server-Zeiteinstellungen
* Ein Problem mit dem Sitzungsspeicher

Suchen Sie im folgenden Abschnitt nach Lösungen.

## Lösung

### Überprüfen auf Probleme mit den Server-Zeiteinstellungen

Überprüfen Sie den in der `admin_user_session` erstellten Sitzungsdatensatz. Wenn die Werte von `created_at` und/oder `updated_at` falsch sind, kann dies durch ein Problem mit den Server-Zeiteinstellungen verursacht werden. Bitten Sie Ihren Server-Systemadministrator, dies zu überprüfen. Beachten Sie, dass die Zeit in DB standardmäßig auf UTC eingestellt ist.

### Ändern des Sitzungsspeichers

Versuchen Sie, den Sitzungsspeicher zu ändern. Verwenden Sie die Informationen aus dem Artikel [So finden Sie Ihre Sitzungsdateien](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/storage/session-storage/sessions) in unserer Entwicklerdokumentation, um herauszufinden, wo Ihre Sitzung gespeichert ist, und ändern Sie sie, indem Sie die `app/etc/env.php`-Datei bearbeiten.

Um beispielsweise mit dem Speichern einer Sitzung im Dateisystem zu beginnen, ändern Sie den Abschnitt `'session'` wie folgt:

```php
....
'session' =>
    array (
      'save' => 'files',
),
....
```

Führen Sie den `bin/magento app:config:import` Befehl aus, um Konfigurationsdaten zu importieren.


## Verwandtes Lesen

* [Daten aus Konfigurationsdateien importieren](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/cli/configuration-management/import-configuration) in unserer Entwicklerdokumentation
* [Konfigurieren [!DNL Redis]](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/cache/redis/config-redis) in unserer Entwicklerdokumentation
* [Umleiten zurück zum [!UICONTROL Commerce Admin]-Anmeldeformular mit dem Fehler „Ihr Konto ist vorübergehend deaktiviert“ ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error) unserer Support-Wissensdatenbank
* [Führen Sie ohne Fehler zurück zum Anmeldeformular, wenn Sie versuchen, sich bei der [!UICONTROL Commerce Admin]](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin) in unserer Support-Wissensdatenbank anzumelden
* [Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/de/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook

