---
title: Überwachen des Factsheet für  [!DNL Adobe Commerce on cloud pro infrastructure]
description: Dieses Dokument enthält Informationen zur Überwachung der Adobe Commerce-Infrastruktur und zu Benachrichtigungen.
exl-id: 01342d8d-2123-4455-b1a5-a08a5805b046
feature: Cloud
source-git-commit: 4926bcff19b8c4c7e2a9a9dfb0cb1fc72a9821ba
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---


# Überwachen des Factsheet für [!DNL Adobe Commerce on cloud pro infrastructure]

Dieses Dokument enthält Informationen zur Überwachung der Adobe Commerce-Infrastruktur und zu Benachrichtigungen.

Die Überwachung ermöglicht Händlern, Systemintegratoren und internen Adobe-Teams die Fehlerbehebung bei der Site-Verfügbarkeit und unzureichendem Festplattenspeicher.

## Problembehebung und -behebung

Adobe Commerce-Instanzen enthalten im Allgemeinen benutzerdefinierten Code und Konfigurationen. Adobe unterstützt und behebt keine Probleme mit benutzerdefiniertem Code und Konfigurationen. Adobe hilft Händlern bei der Fehlerbehebung und Identifizierung von Problemen in unserer Wissensdatenbank und bietet empfohlene Lösungen und Best Practices für die Prävention und Lösung. Wir empfehlen Händlern und Partnern, die unten stehenden Tabellen zu verwenden, um zu verstehen, was überwacht wird und wer für die Lösung verantwortlich ist.

Wenn Benachrichtigungen ausgelöst werden, löst das Adobe Commerce-Supportteam das Problem aus. Im Rahmen der Testphase werden Fehlerprotokolle und andere Ressourcen analysiert. Basierend auf dem Triage werden zusätzliche [!DNL Zendesk] Tickets entweder für Händler oder Partner (im Fall von benutzerdefinierten Updates) oder für Adobe-Teams erstellt, um das Problem zu beheben.

## Adobe Commerce: Standardüberwachung

Die folgenden Ereignisse werden überwacht und das Adobe Commerce-Team unternimmt die erforderlichen Schritte, um die identifizierten Probleme zu beheben und zu kommunizieren.

## Überwachung der Site-Verfügbarkeit

| Site-Verfügbarkeit | Beschreibung |
|------------|------------|
| **Überwachungsziel** | So verfolgen Sie die Site-Verfügbarkeit. |
| **Instrumentiert für** | Einzelne [!DNL URL] für hohe [!DNL SLA] ausgewählt. |
| **Beschreibung** | Die Site-Verfügbarkeit wird anhand der für die Metrik konfigurierten Schwellenwerte bestimmt. Eine Benachrichtigung über einen Site-Ausfall wird ausgelöst, wenn die Prüfung 10 Minuten lang fehlschlägt und keine aktive Bereitstellung durchgeführt wird. |
| **Benachrichtigungsempfänger** | Händler/Partner und Adobe. |
| **Aktion durch Adobe** | Verantwortlich für das Testen und Beheben des Problems in der Adobe Commerce-Infrastruktur. |
| **Aktion des Händlers** | Verantwortlich für die Behebung des Problems, wenn es durch vom Händler/Partner eingeführte Änderungen oder benutzerspezifischen Code verursacht wurde. Informationen zur Fehlerbehebung finden Sie unter: [Site-Down-Fehlerbehebung](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html). |

## Festplattenüberwachung

| Festplattenüberwachung | Beschreibung |
|------------|------------|
| **Überwachungsziel** | So verfolgen Sie die Speichernutzung. |
| **Instrumentiert für** | [!DNL MySQL] Festplattenpartitionen und Medienspeicherpartitionen. |
| **Metrik** | Der kostenlose Speicherplatz wird jede Minute auf dem Host überwacht. Wenn nur noch 5% oder 2 GB freier Speicherplatz vorhanden ist, wird eine Warnung angezeigt. Der kritische Schwellenwert, der auf den verbleibenden freien Speicherplatz gesetzt wird, beträgt 2 % oder 1 GB. |
| **Beschreibung** | Die Benachrichtigung wird basierend auf den Schwellenwerten gesendet, die um den freien Speicherplatz für den Host konfiguriert sind. Zusätzliche Festplattenspeicher wird automatisch einmal zum entsprechenden Mount ([!DNL MySQL] oder Datenträger) hinzugefügt, um einen Site-Ausfall zu verhindern und dem Händler Zeit zu geben, Speicherplatz zu löschen und/oder Code oder Protokolle zu identifizieren und zu beheben, die zu einer raschen Erhöhung der Festplattenbelegung führen. |
| **Benachrichtigungsempfänger** | Händler/Partner und Adobe. |
| **Aktion durch Adobe** | Erhöhen Sie automatisch das Support-Ticket und zusätzlicher Speicherplatz wird automatisch zum entsprechenden Mount hinzugefügt ([!DNL MySQL] oder Medien), um einen Site-Ausfall zu verhindern. |
| **Aktion des Händlers** | Informationen zum Erhalt laufender Warnungsstufen-Festplattenspeicherplatzwarnungen finden Sie unter: <ul><li>[[!DNL Managed alerts for Adobe Commerce]: Warnhinweis bezüglich der Festplatte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce-disk-warning-alert.html)</li><li>[[!DNL Managed alerts for Adobe Commerce]: Warnungen bezüglich Festplattenkritik](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce-disk-critical-alert.html) </li></ul> |
