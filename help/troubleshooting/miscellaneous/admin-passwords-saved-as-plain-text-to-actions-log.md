---
title: Administratorkennwörter, die als normaler Text im Aktionsprotokoll gespeichert werden
description: Dieser Artikel enthält eine Fehlerbehebung für den Fall, dass ein Commerce-Administrator einen neuen Benutzer mit Administratorrechten erstellt und das Kennwort als Klartext in der Datenbanktabelle "magento_logging_event_changes"gespeichert wird.
exl-id: 0e91198e-66b9-456a-9b75-5986369ed8e6
feature: Admin Workspace, Logs
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Administratorkennwörter, die als normaler Text im Aktionsprotokoll gespeichert werden

Dieser Artikel enthält eine Korrektur für den Fall, dass ein Commerce-Administrator einen neuen Benutzer mit Administratorrechten erstellt und das Kennwort als Nur-Text in der Datenbanktabelle &quot;`magento_logging_event_changes`&quot;gespeichert wird.

Um dieses Sicherheitsproblem zu beheben, installieren Sie das Sicherheitsupdate für Adobe Commerce 2.0.16 und 2.1.9. Nach Anwendung des Sicherheits-Updates werden die Kennwörter verschlüsselt und erscheinen nicht als Text.

## Betroffene Versionen {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Affectedversions}

* Adobe Commerce On-Premise 2.X.X
* Adobe Commerce auf Cloud-Infrastruktur 2.X.X

## Problem {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Issue}

Wenn ein bestehender Commerce-Administrator einen neuen Benutzer mit Administratorrechten über **System** > **Berechtigungen** > **Alle Benutzer** > **Neuen Benutzer hinzufügen** erstellt, wird das (als Bestätigung eingegebene) Kennwort als Nur-Text in der Datenbanktabelle `magento_logging_event_changes` gespeichert.

### Zu reproduzierende Schritte: {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Stepstoreproduce}

1. Melden Sie sich als Administrator an und erstellen Sie einen neuen Benutzer, indem Sie zu diesem Pfad navigieren: **System** > Berechtigungen > **Alle Benutzer**.

   ![add_user_magento_2.4.1.png](assets/add_user_magento_2.4.1.png)

1. Klicken Sie dann auf die Seite **Neuen Benutzer hinzufügen** . Geben Sie bei Aufforderung das Kennwort Ihres aktuellen Administrators an.
1. Gehen Sie zur Seite **System** > **Aktionsprotokoll** > **Bericht** und suchen Sie den letzten Protokolleintrag.
1. Sie können das aktuelle Kennwort sehen, weder verschlüsselt noch gehasht.

## Lösung {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Solution}

Durch die Installation von [Adobe Commerce 2.0.16 und 2.1.9 Security Update](https://magento.com/security/patches/magento-2016-and-219-security-update) wird dieses Problem behoben.

Nach der Installation des Sicherheits-Updates wird das Kennwort verschlüsselt und nicht im Klartext in der Tabelle `magento_logging_event_changes` angezeigt.

## Weitere Informationen {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Moreinformation}

* [Adobe Commerce 2.0.16 und 2.1.9 Sicherheits-Update-Seite](https://magento.com/security/patches/magento-2016-and-219-security-update) in unserem Sicherheitscenter
* [Aktualisieren Sie die Adobe Commerce-Anwendung und die Komponenten](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html) in unserer Entwicklerdokumentation
* [Best Practices für die Änderung von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Playbook für die Commerce-Implementierung
