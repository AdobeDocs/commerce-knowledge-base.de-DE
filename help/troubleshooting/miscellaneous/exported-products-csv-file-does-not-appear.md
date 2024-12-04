---
title: Die .csv-Datei der exportierten Produkte wird nicht angezeigt
description: In diesem Artikel wird das Problem behoben, dass Sie versuchen, den gewünschten Entitätstyp in eine CSV-Datei in Commerce Admin zu exportieren, die Datei jedoch nicht angezeigt wird.
exl-id: 8e3bb65c-ea75-4af4-ad4b-4d94ab219bbb
feature: Cache, Data Import/Export, Products, Variables
role: Developer
source-git-commit: b6f1222918b027eaecda42b767e6f83b2cf0f5d0
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 0%

---

# Die .csv-Datei der exportierten Produkte wird nicht angezeigt

Dieser Artikel bietet eine Lösung für das Problem, dass beim Exportieren des gewünschten Entitätstyps in eine CSV-Datei im Commerce Admin die Datei nicht angezeigt wird.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle [unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problem

<u>Zu reproduzierende Schritte</u>

Voraussetzungen: Die Option **Geheimen Schlüssel zu URLs hinzufügen** ist auf *Ja* eingestellt. Die Option wird im Commerce-Admin unter **Geschäfte** > **Konfiguration** > **Erweitert** > **Admin** > **Sicherheit** konfiguriert.

1. Navigieren Sie im Admin zu &quot;**System**&quot;> &quot;**Datenübertragung**&quot;> &quot;**Export**&quot;.

   ![magento_export_products_2.3.4.png](assets/magento_export_products_2.3.4.png)

1. Auswählen
   * **Entitätstyp**: Die Entität, die exportiert werden soll
   * **Dateiformat exportieren**: *CSV*
   * **Feldeingabe**: Lassen Sie die Option deaktiviert.
1. Klicken Sie auf **Weiter**.
1. Die folgende Meldung wird angezeigt: *&quot;Nachricht wird der Warteschlange hinzugefügt, warten Sie, bis Sie Ihre Datei bald erhalten&quot;*.

<u>Erwartetes Ergebnis</u>

Die .csv-Datei, die den exportierten gewünschten Entitätstyp enthält, wird innerhalb weniger Minuten im Raster angezeigt.

<u>Tatsächliches Ergebnis</u>

Die .csv-Datei, die den exportierten gewünschten Entitätstyp enthält, wird nicht mehr als 10 Minuten im Raster angezeigt.

## Ursache

Ein bekanntes Problem mit der Exportfunktion in der Adobe Commerce-Programmteil-Version 2.3.2.

## Lösung

Es gibt zwei mögliche Lösungen für dieses Problem:

* Deaktivieren Sie die Option Geheimen Schlüssel zur URL hinzufügen .
* Führen Sie den Befehl `bin/magento queue:consumers:start exportProcessor` manuell aus und konfigurieren Sie ihn optional für die Ausführung durch Cron.

Weitere Informationen zu beiden Optionen finden Sie in den folgenden Absätzen.

### Deaktivieren Sie die Option Geheimen Schlüssel zur URL hinzufügen .

1. Navigieren Sie im Admin zu &quot;**Stores**&quot;> &quot;**Konfiguration**&quot;> &quot;**Erweitert**&quot;> &quot;**Admin**&quot;> &quot;**Sicherheit**&quot;.
1. Setzen Sie die Option **Geheimen Schlüssel zu URLs hinzufügen** auf *Nein.*
1. Klicken Sie auf **Konfiguration speichern**.
1. Cache unter **System** > **Tools** > **Cache-Verwaltung** bereinigen oder durch Ausführen von    ```bash    bin/magento cache:clean``` oder im Admin.

### Führen Sie den Exportbefehl manuell aus und fügen Sie ihn optional als Cron-Auftrag hinzu

Um die Exportdatei zu erhalten, führen Sie den Befehl `bin/magento queue:consumers:start exportProcessor` aus. Nach der Ausführung sollte die Datei im Raster angezeigt werden.


Um den Prozess optional als Cron-Auftrag hinzuzufügen, müssen Sie die Variable `CRON_CONSUMERS` zur Datei `.magento.env.yaml` hinzufügen.

#### Prozess als Cron-Auftrag hinzufügen (optional)

1. Stellen Sie sicher, dass Ihr Cron eingerichtet und konfiguriert ist. Weitere Informationen finden Sie unter [Einrichten von Cron-Aufträgen](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) .
1. Führen Sie den folgenden Befehl aus, um eine Liste der Verbraucher in der Nachrichtenwarteschlange zurückzugeben:     `./bin/magento queue:consumers:list`
1. Fügen Sie Ihrer `.magento.env.yaml` -Datei im Stammverzeichnis der Anwendung Folgendes hinzu und schließen Sie die Verbraucher ein, die Sie hinzufügen möchten. Hier ist beispielsweise der für die Exportverarbeitung erforderliche Verbraucher:

   ```yaml
   stage:
       deploy:
           CRON_CONSUMERS_RUNNER:
               cron_run: true
               max_messages: 1000
               consumers:
                   - exportProcessor
   ```

   Pushen Sie dann diese aktualisierte Datei und stellen Sie Ihre Umgebung erneut bereit. Weitere Informationen finden Sie unter [Hinzufügen benutzerdefinierter Cron-Aufträge zu Ihrem Projekt](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#add-custom-cron-jobs-to-your-project) in unserer Entwicklerdokumentation.

>[!NOTE]
>
>Wenn Sie die Datei &quot;`.magento.env.yaml`&quot; für Ihre Umgebung nicht finden können und der Eindruck haben, dass sie gelöscht wurde, müssen Sie eine neue &quot;`.magento.env.yaml`&quot;erstellen. Es kann anfangs leer sein. Sie können dort bei Bedarf Informationen hinzufügen. Verweisen Sie in unserer Entwicklerdokumentation auf die folgenden Artikel: [Umgebungsvariablen für die Bereitstellung konfigurieren](/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) und [Umgebungsvariablen](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html) .

>[!TIP]
>
>Bei [YAML-Dateien](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) wird zwischen Groß- und Kleinschreibung unterschieden und Tabs sind nicht zulässig. Achten Sie darauf, einen konsistenten Einzug in der .magento.env.yaml-Datei zu verwenden, da Ihre Konfiguration sonst nicht wie erwartet funktioniert. Die Beispiele in der Dokumentation und in der Beispieldatei verwenden einen Einzug von zwei Leerzeichen. Überprüfen Sie Ihre Konfiguration mit dem Befehl ece-tools validate .

>[!NOTE]
>
>Bei Adobe Commerce in Cloud Infrastructure Pro-Projekten muss die Funktion [Auto-Crons Feature](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=en#crontab) in Ihrer Adobe Commerce-Cloud-Infrastruktur aktiviert sein, bevor Sie benutzerdefinierte Cron-Aufträge in Staging- und Produktionsumgebungen mit `.magento.app.yaml` hinzufügen können. Wenn diese Funktion nicht aktiviert ist, erstellen Sie [ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), damit der Auftrag für Sie hinzugefügt wird.
