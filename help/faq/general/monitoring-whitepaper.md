---
title: Factsheet zur Überwachung für [!DNL Adobe Commerce on cloud pro infrastructure]
description: Dieses Dokument enthält Informationen zur Überwachung der Adobe Commerce-Infrastruktur und zu Benachrichtigungen.
exl-id: 01342d8d-2123-4455-b1a5-a08a5805b046
feature: Cloud
source-git-commit: 4926bcff19b8c4c7e2a9a9dfb0cb1fc72a9821ba
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---


# Factsheet zur Überwachung für [!DNL Adobe Commerce on cloud pro infrastructure]

Dieses Dokument enthält Informationen zur Überwachung der Adobe Commerce-Infrastruktur und zu Benachrichtigungen.

Die Überwachung ermöglicht Händlern, Systemintegratoren und internen Adobe-Teams die Fehlerbehebung bei Site-Verfügbarkeit und unzureichendem Festplattenspeicher.

## Problembehebung und -behebung

Adobe Commerce-Instanzen enthalten im Allgemeinen benutzerdefinierten Code und Konfigurationen. Adobe unterstützt und behebt keine Probleme mit benutzerdefiniertem Code und Konfigurationen. Adobe hilft Händlern bei der Fehlerbehebung und Identifizierung von Problemen in unserer Wissensdatenbank und bietet empfohlene Lösungen und Best Practices für die Prävention und Lösung. Wir empfehlen Händlern und Partnern, die nachstehenden Tabellen zu verwenden, um zu verstehen, was überwacht wird und wer für die Lösung verantwortlich ist.

Wenn Benachrichtigungen ausgelöst werden, löst das Adobe Commerce-Supportteam das Problem aus. Im Rahmen der Triage werden Fehlerprotokolle und andere Ressourcen analysiert. Basierend auf der Klassifizierung werden zusätzliche [!DNL Zendesk]-Support-Tickets entweder für Händler oder Partner (im Falle benutzerdefinierter Updates) oder für interne Adobe-Teams erstellt, um das Problem zu beheben.

## Adobe Commerce: Standardüberwachung

Die folgenden Ereignisse werden überwacht und das Adobe Commerce-Team unternimmt die erforderlichen Schritte, um identifizierte Probleme zu beheben und zu kommunizieren.

## Überwachung der Site-Verfügbarkeit

| Site-Verfügbarkeit | Beschreibung |
|------------|------------|
| **Überwachungsziel** | Zur Nachverfolgung der Site-Verfügbarkeit. |
| **Instrumentiert am** | Für hohe [!DNL SLA] [!DNL URL] ausgewählt. |
| **Beschreibung** | Die Verfügbarkeit der Site wird anhand der Schwellenwerte bestimmt, die für die -Metrik konfiguriert wurden. Eine Benachrichtigung über einen Site-Ausfall wird ausgelöst, wenn die Prüfung 10 Minuten lang fehlschlägt und keine aktive Bereitstellung in Bearbeitung ist. |
| **Benachrichtigungsempfänger** | Händler/Partner und Adobe. |
| **Aktion nach Adobe** | Verantwortlich für die Klassifizierung und Behebung, wenn das Problem die Adobe Commerce-Infrastruktur betrifft. |
| **Aktion des Händlers** | Verantwortlich für die Behebung des Problems, wenn es durch Änderungen oder benutzerdefinierten Code verursacht wird, der von Händler/Partner eingeführt wurde. Informationen zur Fehlerbehebung finden Sie unter: [Site-Down-](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html). |

## Überwachung des Festplattenspeichers

| Überwachung des Festplattenspeichers | Beschreibung |
|------------|------------|
| **Überwachungsziel** | Zum Nachverfolgen der Speicherplatznutzung. |
| **Instrumentiert am** | [!DNL MySQL] Datenträger- und Mediendatenträgerpartitionen. |
| **metrisch** | Der freie Speicherplatz wird jede Minute auf dem Host überwacht. Es wird gewarnt, wenn nur 5 % oder 2 GB freier Speicherplatz verbleiben. Der kritische Schwellenwert für den verbleibenden freien Speicherplatz beträgt 2 % oder 1 GB. |
| **Beschreibung** | Die Benachrichtigung wird basierend auf den Schwellenwerten gesendet, die für den freien Speicherplatz des Hosts konfiguriert wurden. Zusätzliche Speicherkapazität wird automatisch einmal zur entsprechenden Bereitstellung ([!DNL MySQL] oder Medien) hinzugefügt, um einen Standortausfall zu verhindern und dem Händler Zeit zu geben, Speicherplatz freizugeben und/oder Code oder Protokolle zu identifizieren und aufzulösen, die zu einer raschen Zunahme der Festplattenauslastung führen. |
| **Benachrichtigungsempfänger** | Händler/Partner und Adobe. |
| **Aktion nach Adobe** | Das Support-Ticket automatisch anheben, und der entsprechenden Halterung ([!DNL MySQL] oder Medium) wird automatisch zusätzlicher Speicherplatz hinzugefügt, um einen Ausfall der Site zu verhindern. |
| **Aktion des Händlers** | Informationen zum Empfang von Warnmeldungen bezüglich des aktuellen Festplattenspeicherplatzes finden Sie unter: <ul><li>[[!DNL Managed alerts for Adobe Commerce]: Warnhinweis bezüglich Festplatte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce-disk-warning-alert.html)</li><li>[[!DNL Managed alerts for Adobe Commerce]: Kritischer Warnhinweis auf Festplatte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce-disk-critical-alert.html) </li></ul> |
