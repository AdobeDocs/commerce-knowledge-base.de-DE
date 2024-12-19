---
title: Bereitstellung blockiert mit dem Fehler „Anwendung kann nicht auf den Remote-Cluster hochgeladen werden“
description: 'Dieser Artikel bietet eine Lösung für das Adobe Commerce-Problem, bei dem die Bereitstellung hängen bleibt und die folgende Fehlermeldung im Bereitstellungsprotokoll zu finden ist: *„Fehler: Die Anwendung kann nicht in den Remote-Cluster hochgeladen werden“*.'
exl-id: 30f0ec31-db27-429c-b065-cf7770a72194
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# Bereitstellung blockiert mit dem Fehler „Anwendung kann nicht auf den Remote-Cluster hochgeladen werden“

Dieser Artikel bietet eine Lösung für das Adobe Commerce-Problem, bei dem die Bereitstellung hängen bleibt und die folgende Fehlermeldung im Bereitstellungsprotokoll zu finden ist: *„Fehler: Die Anwendung kann nicht in den Remote-Cluster hochgeladen werden“*.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, alle Versionen

## Problem

<u>Schritte zur Reproduktion</u>:

Trigger-Bereitstellung manuell oder durch eine Zusammenführung, Push-Benachrichtigung oder Synchronisierung Ihrer Umgebung.

<u>Erwartetes Ergebnis</u>:

Bereitstellung wurde erfolgreich abgeschlossen.

<u>Tatsächliches </u>:

Die Bereitstellung bleibt stecken und in der Cloud-Benutzeroberfläche wird die folgende Fehlermeldung angezeigt: *Fehler: Anwendung kann nicht in den Remote-Cluster hochgeladen werden“. Im Bereitstellungsprotokoll nach fehlgeschlagener Bereitstellung wurde der Fehler „503 First Byte Timeout“*.

## Ursache

Das Problem wird durch den Ausfall des verfügbaren Speichers verursacht.

## Lösung

Sie können die Protokollordner bereinigen und/oder den Festplattenspeicher erhöhen.

Verzeichnisse, die für die Bereinigung infrage kommen:

* `var/log`
* `var/report`
* `var/debug/`
* `var`

Weitere Informationen zum Erhöhen des Festplattenspeichers in der Starterplanarchitektur für Adobe Commerce in Cloud-Infrastrukturen finden Sie unter [Erhöhen des Festplattenspeichers für die Integrationsumgebung in der Cloud](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md) in unserer Support-Wissensdatenbank. Die gleichen Anweisungen können verwendet werden, um den Speicherplatz der Adobe Commerce in der Cloud Infrastructure Pro Plan Architecture Integration-Umgebung zu erhöhen. Für Pro Production/Staging müssen Sie [ein Ticket beim Adobe Commerce Support einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket-Submit-a-support-ticket) und mehr Speicherplatz anfordern. In der Regel müssen Sie dies jedoch nicht im Staging/in der Produktion des Pro-Plans tun, da Adobe Commerce diese Parameter für Sie und Warnhinweise überwacht und/oder vertraglich vereinbarte Maßnahmen ergreift.
