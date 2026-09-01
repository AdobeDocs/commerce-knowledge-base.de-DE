---
title: Umleiten zurück zum [!UICONTROL Commerce Admin] Anmeldeformular mit der Fehlermeldung „Ihr Konto ist vorübergehend deaktiviert“
description: 'Dieser Artikel bietet die möglichen Lösungen für das Commerce Admin-Anmeldeproblem, bei dem Sie zurück zum Anmeldeformular mit der folgenden Fehlermeldung geleitet werden: *„Ihr Konto ist vorübergehend deaktiviert“*. Die vorgeschlagene Lösung besteht darin, die Einstellungen der Admin-Benutzerdatenbank zu überprüfen und zu korrigieren.'
exl-id: 1c7ffa1c-1fb1-4f69-9534-77d1e119318a
feature: Admin Workspace, Customer Service
role: Developer
source-git-commit: 9f4777deac8e9d367643158cf6947f4cb61e8fdd
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Umleiten zurück zum [!UICONTROL Commerce Admin] Anmeldeformular mit der Fehlermeldung „Ihr Konto ist vorübergehend deaktiviert“

Dieser Artikel bietet die möglichen Lösungen für das [!UICONTROL Commerce Admin] Anmeldeproblem, bei dem Sie mit der folgenden Fehlermeldung zurück zum Anmeldeformular geleitet werden: *„Ihr Konto ist vorübergehend deaktiviert“*. Die vorgeschlagene Lösung besteht darin, die Einstellungen der Admin-Benutzerdatenbank zu überprüfen und zu korrigieren.

## Betroffene Editionen und Versionen:

Alle Adobe Commerce-Versionen und -Editionen

## Problem

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zur Seite **[!UICONTROL Commerce Admin]** .
1. Geben Sie Ihre Anmeldedaten ein und klicken Sie auf **Anmelden**.

<u>Erwartetes Ergebnis</u>:

Sie werden beim [!UICONTROL Commerce Admin] angemeldet.

<u>Tatsächliches </u>:

Sie werden zurück zum Anmeldeformular weitergeleitet, wobei die folgende Fehlermeldung angezeigt wird: *„Ihr Konto ist vorübergehend deaktiviert. Bitte später erneut versuchen“*.

## Lösung

1. Erstellen Sie eine Datenbanksicherung.
1. Verwenden Sie ein Datenbank-Tool wie [[!DNL phpMyAdmin]](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin) oder greifen Sie manuell über die Befehlszeile auf die Datenbank zu. Überprüfen Sie in der `admin_user` Datenbanktabelle für Ihren Admin-Benutzereintrag, ob `is_active` auf &quot;`1`&quot; eingestellt ist und `lock_expires` `NULL` ist. Setzen Sie diese Werte ggf. zurück.

## Verwandtes Lesen

* [Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook
