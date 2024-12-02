---
title: Fehler "Aktuelle Version von RDBMS nicht unterstützt"bei der Implementierung
description: 'Dieser Artikel bietet eine Lösung für den Fall, dass eine Bereitstellung fehlschlägt und Sie im Bereitstellungsprotokoll den folgenden Fehler haben: *Die aktuelle Version von RDBMS wird nicht unterstützt*.'
exl-id: e7300f64-5749-4de8-b4d2-bc4789437282
feature: Deploy
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---

# Fehler &quot;Aktuelle Version von RDBMS nicht unterstützt&quot;bei der Implementierung

Dieser Artikel bietet eine Lösung für den Fall, dass eine Bereitstellung fehlschlägt und Sie im Bereitstellungsprotokoll den folgenden Fehler haben: *Die aktuelle Version von RDBMS wird nicht unterstützt*.

## Betroffene Produkte und Versionen

Adobe Commerce on Cloud Infrastructure, 2.3.0-2.3.7-p1, 2.4.0-2.4.3.

## Problem

Diese Fehlermeldung bedeutet, dass die aktuelle MariaDB-Version in der Adobe Commerce-Version, auf die Sie ein Upgrade durchführen möchten, nicht mehr unterstützt wird und MariaDB auf eine kompatible Version aktualisiert werden muss.


<u>Zu reproduzierende Schritte</u>:

Versuchen Sie, sie bereitzustellen.

<u>Erwartetes Ergebnis</u>:

Erfolgreiche Implementierung.

<u>Tatsächliches Ergebnis</u>:

Die Bereitstellung schlägt mit der Fehlermeldung fehl: *Die aktuelle Version von RDBMS wird nicht unterstützt*.

## Ursache

Ihre MariaDB-Version ist nicht mit der Adobe Commerce-Version kompatibel, auf die Sie ein Upgrade durchführen möchten.

## Lösung

Sie müssen den MariaDB-Dienst auf eine kompatible Version aktualisieren, bevor Sie die Anwendung aktualisieren.


Für die Integrationsverzweigung in Adobe Commerce auf der Cloud-Infrastruktur Pro-Planarchitektur (und allen Zweigen in der Starter-Architektur) folgen Sie den Anweisungen in [Dienst konfigurieren](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/services-yaml) in unserer Entwicklerdokumentation.

Für die Planarchitektur Staging und Produktion in Adobe Commerce on Cloud Infrastructure Pro senden Sie ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), um eine Aktualisierung der Dienste vor der Bereitstellung des Adobe Commerce-Versionsupgrades anzufordern.[


## Verwandtes Lesen

* [Best Practices für Builds und Bereitstellung](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices#best-practices) in unserer Entwicklerdokumentation.
* [Adobe Commerce 2.3.5-Upgrade: kompakt in dynamische Tabellen](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html) in unserer Knowledgebase der Unterstützung.
