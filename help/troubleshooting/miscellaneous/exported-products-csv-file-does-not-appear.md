---
title: Die .csv-Datei der exportierten Produkte wird nicht angezeigt
description: In diesem Artikel wird das Problem behoben, dass Sie versuchen, Produkte in eine CSV-Datei in Commerce Admin zu exportieren, die Datei jedoch nicht angezeigt wird.
exl-id: 8e3bb65c-ea75-4af4-ad4b-4d94ab219bbb
feature: Cache, Data Import/Export, Products, Variables
role: Developer
source-git-commit: d55702ab97f3770d0ec71322f6c24448f0169ad4
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---

# Die .csv-Datei der exportierten Produkte wird nicht angezeigt

In diesem Artikel wird das Problem behoben, dass Sie versuchen, Produkte in eine CSV-Datei in Commerce Admin zu exportieren, die Datei jedoch nicht angezeigt wird.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle [unterstützte Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problem

<u>Zu reproduzierende Schritte</u>

Voraussetzungen: Die **Geheimen Schlüssel zu URLs hinzufügen** ist auf *Ja*. Die Option wird im Commerce Admin unter **Stores** > **Konfiguration** > **Erweitert** > **Admin** > **Sicherheit**.

1. Navigieren Sie im Admin zu **System** > **Datenübertragung** > **Export**.

   ![magento_export_products_2.3.4.png](assets/magento_export_products_2.3.4.png)

1. Auswählen
   * **Entitätstyp**: *Produkte*
   * **Dateiformat exportieren**: *CSV*
   * **Feldumgebung**: Lassen Sie die Option deaktiviert.
1. Klicks **Weiter**.
1. Die folgende Meldung wird angezeigt: *&quot;Meldung wird der Warteschlange hinzugefügt, warten Sie, bis Sie Ihre Datei bald erhalten.&quot;*.

<u>Erwartetes Ergebnis</u>

Die .csv -Datei mit den exportierten Produkten wird in wenigen Minuten im Raster angezeigt.

<u>Tatsächliches Ergebnis</u>

Die .csv -Datei mit den exportierten Produkten wird nicht mehr als 10 Minuten im Raster angezeigt.

## Ursache

Ein bekanntes Problem mit der Exportfunktion in der Adobe Commerce-Programmteil-Version 2.3.2.

## Lösung

Es gibt zwei mögliche Lösungen für dieses Problem:

* Deaktivieren Sie die Option Geheimen Schlüssel zur URL hinzufügen .
* Führen Sie die `bin/magento queue:consumers:start exportProcessor` -Befehl manuell ausführen und optional konfigurieren, dass sie von Cron ausgeführt werden.

Weitere Informationen zu beiden Optionen finden Sie in den folgenden Absätzen.

### Deaktivieren Sie die Option Geheimen Schlüssel zur URL hinzufügen .

1. Navigieren Sie im Admin zu **Stores** > **Konfiguration** > **Erweitert** > **Admin** > **Sicherheit**.
1. Legen Sie die **Geheimen Schlüssel zu URLs hinzufügen** -Option *Anzahl*
1. Klicks **Konfiguration speichern**.
1. Cache unter leeren **System** > **Instrumente** > **Cacheverwaltung** oder durch Ausführen    ```bash    bin/magento cache:clean``` oder im Admin.

### Führen Sie den Exportbefehl manuell aus und fügen Sie ihn optional als Cron-Auftrag hinzu

Führen Sie zum Abrufen der Exportdatei den `bin/magento queue:consumers:start exportProcessor` Befehl. Nach der Ausführung sollte die Datei im Raster angezeigt werden.


Um den Prozess optional als Cron-Auftrag hinzuzufügen, müssen Sie die `CRON_CONSUMERS` in die `.magento.env.yaml` -Datei.

#### Prozess als Cron-Auftrag hinzufügen (optional)

1. Stellen Sie sicher, dass Ihr Cron eingerichtet und konfiguriert ist. Siehe [Einrichten von Cron-Aufträgen](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) für Details.
1. Führen Sie den folgenden Befehl aus, um eine Liste der Verbraucher in der Nachrichtenwarteschlange zurückzugeben:     `./bin/magento queue:consumers:list`
1. Fügen Sie Folgendes zu Ihrer `.magento.env.yaml` im Stammverzeichnis der Anwendung und schließen Sie die Verbraucher ein, die Sie hinzufügen möchten. Hier ist beispielsweise der für die Exportverarbeitung erforderliche Verbraucher:

   ```yaml
   stage:
       deploy:
           CRON_CONSUMERS_RUNNER:
               cron_run: true
               max_messages: 1000
               consumers:
                   - exportProcessor
   ```

   Pushen Sie dann diese aktualisierte Datei und stellen Sie Ihre Umgebung erneut bereit. Referenz [Hinzufügen benutzerdefinierter Cron-Aufträge zu Ihrem Projekt](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#add-custom-cron-jobs-to-your-project) in unserer Entwicklerdokumentation.

>[!NOTE]
>
>Wenn die Variable `.magento.env.yaml` -Datei für Ihre Umgebung erstellen und Sie glauben, dass sie gelöscht wurde, müssen Sie eine neue `.magento.env.yaml`. Es kann anfangs leer sein. Sie können dort bei Bedarf Informationen hinzufügen. Verweisen Sie auf die folgenden Artikel: [Umgebungsvariablen für die Bereitstellung konfigurieren](/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) und [Umgebungsvariablen](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html) in unserer Entwicklerdokumentation.

>[!TIP]
>
>[YAML-Dateien](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) zwischen Groß- und Kleinschreibung unterscheiden und keine Tabs zulassen. Achten Sie darauf, einen konsistenten Einzug in der .magento.env.yaml-Datei zu verwenden, da Ihre Konfiguration sonst nicht wie erwartet funktioniert. Die Beispiele in der Dokumentation und in der Beispieldatei verwenden einen Einzug von zwei Leerzeichen. Überprüfen Sie Ihre Konfiguration mit dem Befehl ece-tools validate .

>[!NOTE]
>
>Bei Adobe Commerce zu Cloud-Infrastruktur-Pro-Projekten wird die [Funktion &quot;Auto-Crons&quot;](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=en#crontab) muss in Ihrer Adobe Commerce in der Cloud-Infrastruktur aktiviert sein, bevor Sie benutzerdefinierte Cron-Aufträge zu Staging- und Produktionsumgebungen hinzufügen können, indem Sie `.magento.app.yaml`. Wenn diese Funktion nicht aktiviert ist, [Support-Ticket erstellen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), damit der Auftrag für Sie hinzugefügt wird.
