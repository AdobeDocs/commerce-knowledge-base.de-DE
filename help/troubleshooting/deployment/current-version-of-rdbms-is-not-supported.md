---
title: Fehler „Aktuelle Version von RDBMS wird nicht unterstützt“ bei der Bereitstellung
description: 'Dieser Artikel bietet eine Lösung für den Fall, dass eine Bereitstellung fehlschlägt und Sie den folgenden Fehler im Bereitstellungsprotokoll haben: *Die aktuelle Version von RDBMS wird nicht unterstützt*.'
exl-id: e7300f64-5749-4de8-b4d2-bc4789437282
feature: Deploy
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---

# Fehler „Aktuelle Version von RDBMS wird nicht unterstützt“ bei der Bereitstellung

Dieser Artikel bietet eine Lösung für den Fall, dass eine Bereitstellung fehlschlägt und Sie den folgenden Fehler im Bereitstellungsprotokoll haben: *Aktuelle Version von RDBMS wird nicht unterstützt*.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur, 2.3.0-2.3.7-p1, 2.4.0-2.4.3.

## Problem

Diese Fehlermeldung bedeutet, dass die aktuelle MariaDB-Version in der Adobe Commerce-Version, auf die Sie ein Upgrade durchführen möchten, nicht mehr unterstützt wird und MariaDB auf eine kompatible Version aktualisiert werden muss.


<u>Schritte zur Reproduktion</u>:

Versuchen Sie, bereitzustellen.

<u>Erwartetes Ergebnis</u>:

Erfolgreiche Bereitstellung.

<u>Tatsächliches </u>:

Die Bereitstellung schlägt mit folgender Fehlermeldung fehl: *Aktuelle Version von RDBMS wird nicht unterstützt*.

## Ursache

Ihre Version von MariaDB ist nicht kompatibel mit der Version von Adobe Commerce, auf die Sie ein Upgrade durchführen möchten.

## Lösung

Sie müssen den MariaDB-Dienst auf eine kompatible Version aktualisieren, bevor Sie die Anwendung aktualisieren.


Für die Integrationsverzweigung auf Adobe Commerce in der Cloud-Infrastruktur Pro Planarchitektur (und alle Verzweigungen in der Starterarchitektur) folgen Sie bitte [Service konfigurieren](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/services-yaml) in unserer Entwicklerdokumentation.

Für die Planarchitektur Staging und Produktion in Adobe Commerce auf Cloud-Infrastruktur Pro [ Sie ein Support-Ticket ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), um anzufordern, dass die Services vor der Bereitstellung des Adobe Commerce-Versions-Upgrades aktualisiert werden.


## Verwandtes Lesen

* [Best Practices für Builds und ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices#best-practices)) in unserer Entwicklerdokumentation.
* [Adobe Commerce-Upgrade 2.3.5: Kompakt auf dynamische Tabellen](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html) in unserer Support-Wissensdatenbank.
