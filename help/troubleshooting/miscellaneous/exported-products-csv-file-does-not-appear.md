---
title: Exportierte .csv-Produktdatei wird nicht angezeigt
description: Dieser Artikel bietet eine Lösung für das Problem, dass Sie versuchen, den gewünschten Entitätstyp in eine CSV-Datei im Commerce-Admin zu exportieren, die Datei jedoch nicht angezeigt wird.
exl-id: 8e3bb65c-ea75-4af4-ad4b-4d94ab219bbb
feature: Cache, Data Import/Export, Products, Variables
role: Developer
source-git-commit: b6f1222918b027eaecda42b767e6f83b2cf0f5d0
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 0%

---

# Exportierte .csv-Produktdatei wird nicht angezeigt

Dieser Artikel bietet eine Lösung für den Fall, dass der Export des gewünschten Entitätstyps in eine CSV-Datei in der Commerce Admin dazu führt, dass die Datei nicht angezeigt wird.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, alle [unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problem

<u>Schritte zur Reproduktion</u>

Voraussetzungen: Die Option **Geheimen Schlüssel zu URLs hinzufügen** ist auf &quot;*&quot;*. Die Option wird im Commerce Admin unter **Stores** > **Configuration** > **Advanced** > **Admin** > **Security** konfiguriert.

1. Navigieren Sie in der Admin zu **System** > **Datenübertragung** > **Exportieren**.

   ![magento_export_products_2.3.4.png](assets/magento_export_products_2.3.4.png)

1. Auswählen
   * **Entitätstyp**: Die zu exportierende Entität
   * **Dateiformat exportieren**: *CSV*
   * **Feldgehäuse**: nicht markieren.
1. Klicken Sie **Weiter**.
1. Die folgende Meldung wird angezeigt: *„Nachricht wird der Warteschlange hinzugefügt, bitte warten, bis die Datei bald verfügbar ist“*.

<u>Erwartetes Ergebnis</u>

Die CSV-Datei, die den exportierten gewünschten Entitätstyp enthält, wird innerhalb weniger Minuten im Raster angezeigt.

<u>Tatsächliches Ergebnis</u>

Die CSV-Datei, die den exportierten gewünschten Entitätstyp enthält, wird nicht in 10 Minuten oder länger im Raster angezeigt.

## Ursache

Ein bekanntes Problem mit der Exportfunktion in der Adobe Commerce-Programmteilversion 2.3.2.

## Lösung

Es gibt zwei mögliche Lösungen für dieses Problem:

* Deaktivieren Sie die Option Geheimen Schlüssel zur URL hinzufügen .
* Führen Sie den `bin/magento queue:consumers:start exportProcessor` Befehl manuell aus und konfigurieren Sie ihn optional so, dass er von cron ausgeführt wird.

Weitere Informationen zu beiden Optionen finden Sie in den folgenden Absätzen.

### Deaktivieren Sie die Option Geheimen Schlüssel zur URL hinzufügen .

1. Navigieren Sie in Admin zu **Stores** > **Konfiguration** > **Erweitert** > **Admin** > **Sicherheit**.
1. Setzen Sie die **Geheimschlüssel zu URLs hinzufügen** auf *Nein.*
1. Klicken Sie **Konfiguration speichern**.
1. Bereinigen Sie den Cache unter **System** > **Tools** > **Cache-Verwaltung** oder indem Sie Folgendes ausführen    ```bash    bin/magento cache:clean``` oder in der Admin.

### Führen Sie den Exportbefehl manuell aus und fügen Sie ihn optional als Cron-Auftrag hinzu

Um die Exportdatei abzurufen, führen Sie den `bin/magento queue:consumers:start exportProcessor` Befehl aus. Danach sollte die Datei im Raster angezeigt werden.


Um den Prozess optional als Cron-Auftrag hinzuzufügen, müssen Sie die `CRON_CONSUMERS` Variable zur `.magento.env.yaml`-Datei hinzufügen.

#### Prozess als Cron-Auftrag hinzufügen (optional)

1. Stellen Sie sicher, dass Ihr Cron eingerichtet und konfiguriert ist. Weitere [ finden Sie unter „Einrichten ](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) Cron-Aufträgen“.
1. Führen Sie den folgenden Befehl aus, um eine Liste der Nachrichtenwarteschlangen-Verbraucher zurückzugeben:     `./bin/magento queue:consumers:list`
1. Fügen Sie Ihrer `.magento.env.yaml`-Datei im Stammverzeichnis der Anwendung Folgendes hinzu und schließen Sie die Verbraucher ein, die Sie hinzufügen möchten. Hier finden Sie beispielsweise den Verbraucher, der für die Exportverarbeitung erforderlich ist:

   ```yaml
   stage:
       deploy:
           CRON_CONSUMERS_RUNNER:
               cron_run: true
               max_messages: 1000
               consumers:
                   - exportProcessor
   ```

   Pushen Sie dann diese aktualisierte Datei und stellen Sie Ihre Umgebung erneut bereit. Verweisen Sie auch [Benutzerdefinierte Cron-Aufträge zu Ihrem Projekt hinzufügen](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#add-custom-cron-jobs-to-your-project) in unserer Entwicklerdokumentation.

>[!NOTE]
>
>Wenn Sie die `.magento.env.yaml`-Datei für Ihre Umgebung nicht finden können und der Meinung sind, dass sie gelöscht wurde, müssen Sie eine neue `.magento.env.yaml` erstellen. Möglicherweise ist es zunächst leer. Sie können dort nach Bedarf weitere Informationen hinzufügen. Verweisen Sie auf die folgenden Artikel[ „Konfigurieren von Umgebungsvariablen für ](/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html)&quot; und [Umgebungsvariablen](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html) in Ihrer Entwicklerdokumentation.

>[!TIP]
>
>[YAML-Dateien](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) wird zwischen Groß- und Kleinschreibung unterschieden und es werden keine Registerkarten zugelassen. Achten Sie darauf, in der gesamten Datei &quot;.magento.env.yaml“ einen konsistenten Einzug zu verwenden. Andernfalls funktioniert Ihre Konfiguration möglicherweise nicht wie erwartet. Die Beispiele in der Dokumentation und in der Beispieldatei verwenden eine Einrückung mit zwei Leerzeichen. Verwenden Sie den Befehl ECE-Tools validate , um Ihre Konfiguration zu überprüfen.

>[!NOTE]
>
>In Adobe Commerce in Cloud Infrastructure Pro-Projekten muss die Funktion [automatische Krone](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=en#crontab) in Ihrer Adobe Commerce in der Cloud-Infrastruktur aktiviert sein, bevor Sie mithilfe von `.magento.app.yaml` benutzerdefinierte Cron-Aufträge zu Staging- und Produktionsumgebungen hinzufügen können. Wenn diese Funktion nicht aktiviert ist[ erstellen Sie ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), damit der Auftrag für Sie hinzugefügt wird.
