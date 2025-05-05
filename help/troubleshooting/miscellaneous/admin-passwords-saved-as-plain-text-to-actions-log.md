---
title: Admin-Kennwörter im Aktionsprotokoll als Nur-Text gespeichert
description: Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass ein Commerce-Administrator einen neuen Benutzer mit Administratorrechten erstellt und das Kennwort als Nur-Text in der Datenbanktabelle „magento_logging_event_changes“ gespeichert wird.
exl-id: 0e91198e-66b9-456a-9b75-5986369ed8e6
feature: Admin Workspace, Logs
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Admin-Kennwörter im Aktionsprotokoll als Nur-Text gespeichert

Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass ein Commerce-Administrator einen neuen Benutzer mit Administratorrechten erstellt und das Kennwort als Nur-Text in der `magento_logging_event_changes`-Datenbanktabelle gespeichert wird.

Um dieses Sicherheitsproblem zu beheben, installieren Sie das Sicherheitsupdate Adobe Commerce 2.0.16 und 2.1.9. Nach der Anwendung des Sicherheits-Updates werden die Kennwörter verschlüsselt und nicht als Klartext angezeigt.

## Betroffene Versionen {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Affectedversions}

* Adobe Commerce On-Premises 2.X.X
* Adobe Commerce auf Cloud-Infrastruktur 2.x.x

## {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Issue}

Wenn ein bestehender Commerce-Administrator einen neuen Benutzer mit Administratorrechten über **System** > **Berechtigungen** > **Alle Benutzer** > **Neuen Benutzer hinzufügen** erstellt, wird das Kennwort (eingegeben als Bestätigung) als Nur-Text in der `magento_logging_event_changes` Datenbanktabelle gespeichert.

### Schritte zur Reproduktion: {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Stepstoreproduce}

1. Melden Sie sich als Administrator an und erstellen Sie einen neuen Benutzer, indem Sie zu diesem Pfad navigieren: **System** > Berechtigungen > **Alle Benutzer**.

   ![add_user_magento_2.4.1.png](assets/add_user_magento_2.4.1.png)

1. Klicken Sie dann auf **Seite „Neuen Benutzer hinzufügen**. Geben Sie das Kennwort Ihres aktuellen Administrators ein, wenn Sie dazu aufgefordert werden.
1. Navigieren Sie zur Seite **System** > **Aktionsprotokoll** > **Bericht** und suchen Sie den letzten Protokolleintrag.
1. Sie können das aktuelle Kennwort sehen, weder verschlüsselt noch gehasht.

## {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Solution}

Dieses Problem wurde durch die Installation des Sicherheitsupdates [Adobe Commerce 2.0.16 und ](https://magento.com/security/patches/magento-2016-and-219-security-update).1.9 behoben.

Nach der Installation des Sicherheits-Updates wird das Kennwort verschlüsselt und nicht im Klartext in der `magento_logging_event_changes` angezeigt.

## Weitere Informationen {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Moreinformation}

* [Seite mit den Sicherheitsupdates für Adobe Commerce 2.0.16 und 2.1.9](https://magento.com/security/patches/magento-2016-and-219-security-update) in unserem Sicherheitscenter
* [Aktualisieren des Adobe Commerce-Programms und der Komponenten](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html?lang=de) in unserer Entwicklerdokumentation
* [Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/de/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook
