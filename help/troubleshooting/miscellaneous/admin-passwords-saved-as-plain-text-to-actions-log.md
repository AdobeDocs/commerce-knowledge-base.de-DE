---
title: Administratorkennwörter, die als normaler Text im Aktionsprotokoll gespeichert werden
description: Dieser Artikel enthält eine Fehlerbehebung für den Fall, dass ein Commerce-Administrator einen neuen Benutzer mit Administratorrechten erstellt und das Kennwort als Klartext in der Datenbanktabelle "magento_logging_event_changes"gespeichert wird.
exl-id: 0e91198e-66b9-456a-9b75-5986369ed8e6
feature: Admin Workspace, Logs
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Administratorkennwörter, die als normaler Text im Aktionsprotokoll gespeichert werden

Dieser Artikel enthält eine Fehlerbehebung für das Erstellen eines neuen Benutzers durch einen Commerce-Administrator mit Administratorrechten und das Kennwort wird als Nur-Text im `magento_logging_event_changes` Datenbanktabelle.

Um dieses Sicherheitsproblem zu beheben, installieren Sie das Sicherheitsupdate für Adobe Commerce 2.0.16 und 2.1.9. Nach Anwendung des Sicherheits-Updates werden die Kennwörter verschlüsselt und erscheinen nicht als Text.

## Betroffene Versionen {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Affectedversions}

* Adobe Commerce On-Premise 2.X.X
* Adobe Commerce auf Cloud-Infrastruktur 2.X.X

## Problem {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Issue}

Wenn ein bestehender Commerce-Administrator einen neuen Benutzer erstellt, der über die Administratorrechte verfügt **System** > **Berechtigungen** > **Alle Benutzer** > **Neuen Benutzer hinzufügen**, wird das (als Bestätigung eingegebene) Kennwort als Nur-Text im `magento_logging_event_changes` Datenbanktabelle.

### Zu reproduzierende Schritte: {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Stepstoreproduce}

1. Melden Sie sich als Administrator an und erstellen Sie einen neuen Benutzer, indem Sie zu diesem Pfad navigieren: **System** > Berechtigungen > **Alle Benutzer**.

   ![add_user_magento_2.4.1.png](assets/add_user_magento_2.4.1.png)

1. Klicken Sie anschließend auf **Neuen Benutzer hinzufügen** Seite. Geben Sie bei Aufforderung das Kennwort Ihres aktuellen Administrators an.
1. Navigieren Sie zu **System** > **Aktionsprotokoll** > **Bericht** und suchen Sie den letzten Protokolleintrag.
1. Sie können das aktuelle Kennwort sehen, weder verschlüsselt noch gehasht.

## Lösung {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Solution}

Installieren der [Sicherheitsupdate für Adobe Commerce 2.0.16 und 2.1.9](https://magento.com/security/patches/magento-2016-and-219-security-update) behebt dieses Problem.

Nach der Installation des Sicherheits-Updates wird das Kennwort verschlüsselt und nicht im Klartext im `magento_logging_event_changes` Tabelle.

## Weitere Informationen {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Moreinformation}

[Adobe Commerce 2.0.16 und 2.1.9 Sicherheits-Update-Seite](https://magento.com/security/patches/magento-2016-and-219-security-update) in unserem Sicherheitszentrum.

[Aktualisieren der Adobe Commerce-Anwendung und -Komponenten](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html) in unserer Entwicklerdokumentation.
