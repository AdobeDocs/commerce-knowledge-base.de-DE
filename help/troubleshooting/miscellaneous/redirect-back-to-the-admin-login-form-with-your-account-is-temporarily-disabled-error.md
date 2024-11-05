---
title: '''Weiterleiten zum [!UICONTROL Commerce Admin] Anmeldeformular mit dem Fehler "Ihr Konto ist vorübergehend deaktiviert"'
description: '"Dieser Artikel bietet die möglichen Lösungen für das Commerce Admin-Anmeldeproblem, bei dem Sie mit der folgenden Fehlermeldung zurück zum Anmeldeformular weitergeleitet werden: *"Ihr Konto ist vorübergehend deaktiviert"*. Die empfohlene Lösung besteht darin, die Einstellungen der Admin-Benutzerdatenbank zu überprüfen und zu korrigieren."'
exl-id: 1c7ffa1c-1fb1-4f69-9534-77d1e119318a
feature: Admin Workspace, Customer Service
role: Developer
source-git-commit: f87263cde5aa001f78abc368c949ce150feecb91
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# Gehen Sie zurück zum Anmeldeformular [!UICONTROL Commerce Admin] mit dem Fehler &quot;Ihr Konto ist vorübergehend deaktiviert&quot;.

Dieser Artikel enthält die möglichen Lösungen für das [!UICONTROL Commerce Admin] -Anmeldeproblem, bei dem Sie zum Anmeldeformular zurückgeleitet werden und die folgende Fehlermeldung angezeigt wird: *&quot;Ihr Konto ist vorübergehend deaktiviert&quot;*. Die empfohlene Lösung besteht darin, die Einstellungen der Admin-Benutzerdatenbank zu überprüfen und zu korrigieren.

## Betroffene Versionen:

Alle Adobe Commerce-Versionen und -Editionen

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zur Seite &quot;**[!UICONTROL Commerce Admin]**&quot;.
1. Geben Sie Ihre Anmeldedaten ein und klicken Sie auf **Anmelden**.

<u>Erwartetes Ergebnis</u>:

Sie werden bei [!UICONTROL Commerce Admin] angemeldet.

<u>Tatsächliches Ergebnis</u>:

Sie werden zum Anmeldeformular zurückgeleitet, wobei die folgende Fehlermeldung angezeigt wird: *&quot;Ihr Konto ist vorübergehend deaktiviert. Versuchen Sie es später erneut&quot;*.

## Lösung

1. Erstellen Sie eine Datenbanksicherung.
1. Verwenden Sie ein Datenbank-Tool wie [[!DNL phpMyAdmin]](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/optional.html#install-optional-phpmyadmin) oder greifen Sie manuell über die Befehlszeile auf die DB zu. Überprüfen Sie in der Datenbanktabelle `admin_user` für Ihren Administratorbenutzerdatensatz, ob `is_active` auf &quot;`1`&quot; und `lock_expires` auf &quot;`NULL`&quot; gesetzt ist. Setzen Sie diese Werte bei Bedarf zurück.

## Verwandtes Lesen

* [Kehren Sie beim Versuch, sich bei [!UICONTROL Commerce Admin]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin) anzumelden, ohne Fehler zum Anmeldeformular zurück.
* [Best Practices für die Änderung von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Playbook für die Commerce-Implementierung
