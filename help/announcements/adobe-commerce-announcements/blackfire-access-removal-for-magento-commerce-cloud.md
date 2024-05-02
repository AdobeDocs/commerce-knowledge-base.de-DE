---
title: Entfernung von Blackfire-Zugriff für Adobe Commerce in der Cloud-Infrastruktur
description: Ab dem 11. April 2020 ist der kostenlose Zugriff auf die Blackfire-Leistungsüberwachung nicht mehr in Adobe Commerce über die Cloud Infrastructure Pro-Planarchitektur oder Adobe Commerce über die Abonnements der Cloud Infrastructure Starter-Architekturstruktur enthalten.  Sie können sich nicht mehr bei Ihrem Blackfire-Konto anmelden. Es ist möglich, Blackfire auch nach dem 11. April weiter zu verwenden, indem Sie direkt über Blackfire.io eine Lizenz erwerben. Adobe Commerce-Händler, die bis zu diesem Zeitpunkt keine Lizenzen direkt bei Blackfire erworben haben, werden ihre kostenlosen, von Adobe bereitgestellten Blackfire-Lizenzen deaktivieren. Gleichzeitig wird die Funktion zum Erstellen neuer Berichte mithilfe des Profiler-Tools deaktiviert. Kunden, die die auf Cloud-Infrastrukturen gehostete Pro-Architektur nutzen, können die Infrastrukturleistung weiterhin kostenlos über New Relic Infrastructure überwachen.
exl-id: bf33c2c6-e9b3-474a-a127-909b51dff92f
feature: Cloud, Paas
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# Entfernung von Blackfire-Zugriff für Adobe Commerce in der Cloud-Infrastruktur

Ab dem 11. April 2020 ist der kostenlose Zugriff auf die Blackfire-Leistungsüberwachung nicht mehr in Adobe Commerce über die Cloud Infrastructure Pro-Planarchitektur oder Adobe Commerce über die Abonnements der Cloud Infrastructure Starter-Architekturstruktur enthalten.  Sie können sich nicht mehr bei Ihrem Blackfire-Konto anmelden. Es ist möglich, Blackfire auch nach dem 11. April weiter zu verwenden, indem Sie direkt über Blackfire.io eine Lizenz erwerben. Adobe Commerce-Händler, die bis zu diesem Zeitpunkt keine Lizenzen direkt bei Blackfire erworben haben, werden ihre kostenlosen, von Adobe bereitgestellten Blackfire-Lizenzen deaktivieren. Gleichzeitig wird die Funktion zum Erstellen neuer Berichte mithilfe des Profiler-Tools deaktiviert. Kunden, die die auf Cloud-Infrastrukturen gehostete Pro-Architektur nutzen, können die Infrastrukturleistung weiterhin kostenlos über New Relic Infrastructure überwachen.

**Wenn Sie weiterhin Blackfire verwenden möchten**:

1. Sie müssen eine Lizenz direkt bei Blackfire erwerben.
1. Einrichten von Blackfire mithilfe dieser [Schritte](https://blackfire.io/docs/integrations/paas/magentocloud).
1. Sollten Sie Schwierigkeiten mit der Installation haben, können Sie [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) um Hilfe zu ersuchen. Wenden Sie sich bei Blackfire-spezifischen Fragen direkt an den Blackfire-Support unter [support@blackfire.io](mailto:support@blackfire.io).

## Wenn beim Ausführen einer Bereitstellung Fehler auftreten:

Wenn beim Ausführen einer Bereitstellung Blackfire-bezogene Fehler auftreten, führen Sie folgende Schritte aus:

1. Entfernen Sie Blackfire aus Ihrer Konfiguration. Bearbeiten Sie die `.magento.app.yaml` -Datei und entfernen Sie Blackfire aus dem Laufzeitabschnitt:

   ```YAML
   ...
   # Enable extensions required by Magento 2
   runtime:
     extensions:
     - redis
     - xsl
     - json
     -**blackfire**
      - imap
   ...
   ```

1. Schließen Sie dies in der lokalen Entwicklungsumgebung ab und drücken Sie die Cloud hoch.

Nur [Support-Ticket einreichen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) Wenn nach der Ausführung einer Bereitstellung der folgende Fehler auftritt:

*PHP-Warnung: PHP-Startup: Dynamische Bibliothek &#39;blackfire.so&#39; kann nicht geladen werden (versucht: /usr/lib/php/20180731-zts/blackfire.so (/usr/lib/php/20180731-zts/blackfire.so: kann keine freigegebene Objektdatei öffnen: Keine solche Datei oder Verzeichnis), /usr/lib/php/20180731-zts/blackfire.so.so (/usr/lib/php/20180731-zts/blackfire.so.so: kann keine freigegebene Objektdatei öffnen: Keine solche Datei oder Verzeichnis) in Zeile 0 Unbekannt*

Dieser Fehler bedeutet, dass das Blackfire-Plugin aktualisiert und nicht geladen werden muss.

**Wenn Sie die New Relic-Infrastruktur verwenden möchten**:

Informationen zum Zugriff auf die New Relic-Infrastruktur finden Sie unter [Zugriff auf New Relic](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html) in unserer Wissensdatenbank.
