---
title: Implementierung hängt mit dem Fehler "Anwendung kann nicht in den Remote-Cluster hochgeladen werden"
description: '"Dieser Artikel bietet eine Lösung für das Adobe Commerce-Problem, bei dem die Bereitstellung blockiert wird und die folgende Fehlermeldung im Bereitstellungsprotokoll zu finden ist: *"Fehler: Anwendung kann nicht in den Remote-Cluster hochgeladen werden"*."'
exl-id: 30f0ec31-db27-429c-b065-cf7770a72194
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# Implementierung hängt mit dem Fehler &quot;Anwendung kann nicht in den Remote-Cluster hochgeladen werden&quot;

Dieser Artikel bietet eine Lösung für das Adobe Commerce-Problem, bei dem die Bereitstellung blockiert wird und die folgende Fehlermeldung im Bereitstellungsprotokoll zu finden ist: *&quot;Fehler: Anwendung kann nicht in den Remote-Cluster hochgeladen werden&quot;*.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle Versionen

## Problem

<u>Zu reproduzierende Schritte</u>:

Trigger manuell bereitstellen oder eine Zusammenführung, Push-Benachrichtigung oder Synchronisation Ihrer Umgebung durchführen.

<u>Erwartetes Ergebnis</u>:

Die Implementierung wurde erfolgreich abgeschlossen.

<u>Tatsächliches Ergebnis</u>:

Die Implementierung hängt davon ab, und im Fehlerprotokoll zur Implementierung in der Cloud-Benutzeroberfläche wird die folgende Fehlermeldung angezeigt: *&quot;Fehler: Die Anwendung kann nicht in den Remote-Cluster hochgeladen werden&quot;, der im Bereitstellungsprotokoll nach fehlgeschlagener Bereitstellung gefunden wurde, zeigt die Site möglicherweise den Fehler &quot;503 first byte timeout&quot;an.*.

## Ursache

Das Problem wird durch den Ausfall des verfügbaren Speichers verursacht.

## Lösung

Sie können erwägen, die Protokollverzeichnisse zu bereinigen und/oder den Speicherplatz zu erhöhen.

Für die Bereinigung berücksichtigte Verzeichnisse:

* `var/log`
* `var/report`
* `var/debug/`
* `var`

Weitere Informationen zur Erhöhung des Festplattenspeichers, wenn Sie sich in der Adobe Commerce-Planarchitektur für Cloud-Infrastruktur-Starter befinden, finden Sie unter [Erhöhen Sie den Speicherplatz für die Integrationsumgebung in Cloud.](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md) in unserer Wissensdatenbank. Dieselbe Anleitung kann verwendet werden, um den Raum der Adobe Commerce in der Umgebung der Cloud Infrastructure Pro-Planarchitektur-Integrationsumgebung zu vergrößern. Für Pro Production/Staging müssen Sie [Ticket an den Adobe Commerce-Support senden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket-Submit-a-support-ticket) und fordern Sie mehr Speicherplatz an. In der Regel müssen Sie sich jedoch nicht mit dem Staging/der Produktion des Pro-Plans befassen, da Adobe Commerce diese Parameter für Sie überwacht und Warnungen sendet und/oder vertragsgemäß tätig wird.
