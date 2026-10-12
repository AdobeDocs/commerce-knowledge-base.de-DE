---
title: Umleiten zurück zum [!UICONTROL Commerce Admin] Anmeldeformular mit der Fehlermeldung „Ihr Konto ist vorübergehend deaktiviert“
description: 'Dieser Artikel bietet die möglichen Lösungen für das Commerce Admin-Anmeldeproblem, bei dem Sie zurück zum Anmeldeformular mit der folgenden Fehlermeldung geleitet werden: *„Ihr Konto ist vorübergehend deaktiviert“*. Die vorgeschlagene Lösung besteht darin, die Einstellungen der Admin-Benutzerdatenbank zu überprüfen und zu korrigieren.'
exl-id: 1c7ffa1c-1fb1-4f69-9534-77d1e119318a
feature: Admin Workspace, Customer Service
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: deedbb4d-f1b7-58ea-a34a-de1f481f9d4c
    internal-label: Customer Service
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
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
