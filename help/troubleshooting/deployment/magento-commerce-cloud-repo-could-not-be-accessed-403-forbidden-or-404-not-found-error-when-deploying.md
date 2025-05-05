---
title: 'Zugriff auf Adobe Commerce auf Cloud-Repository nicht möglich: Fehler „403 Verboten“ oder „404 Nicht gefunden“ bei der Bereitstellung'
description: 'In diesem Artikel wird beschrieben, wie Sie den Fehler bei der fehlgeschlagenen Bereitstellung der Adobe Commerce-Cloud-Infrastruktur ähnlich dem folgenden beheben können:'
exl-id: 2f72d80a-05b2-4908-8fa8-61d06885ed07
feature: Cloud, Deploy, Paas, Variables
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 0%

---

# Zugriff auf Adobe Commerce auf Cloud-Repository nicht möglich: Fehler „403 Verboten“ oder „404 Nicht gefunden“ bei der Bereitstellung

In diesem Artikel wird beschrieben, wie Sie den Fehler bei der fehlgeschlagenen Bereitstellung der Adobe Commerce-Cloud-Infrastruktur ähnlich dem folgenden beheben können:

&quot;*Die &#39;https://repo.magento.com/archives/magento/magento-cloud-configuration/magento-magento-cloud-configuration-x.x.x.x.zip&#39; URL konnte nicht aufgerufen werden: HTTP/1.1 403 Verboten* &quot;. Oder die Datei &quot;*https://repo.magento.com/archives/magento/module-customer-segment/magento-module-customer-segment-102.0.5.0-patch2.zip&quot; konnte nicht heruntergeladen werden (HTTP/1.1 404 Not Found)*&quot;.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastrukturen 2.2.x, 2.3.x und 2.4.x

## Problem

Fehlermeldung bei der Bereitstellung, die angibt, dass auf die Repository-URL nicht zugegriffen werden konnte.

<u>Schritte zur Reproduktion</u>

Trigger-Bereitstellung manuell oder durch eine Zusammenführung, Push-Benachrichtigung oder Synchronisierung Ihrer Umgebung.

<u>Tatsächliches Ergebnis</u>

Bereitstellung bleibt stecken. Im Bereitstellungsfehlerprotokoll in der Projekt-Benutzeroberfläche wird eine Fehlermeldung wie die folgende angezeigt:

*„Auf die &#39;https://repo.magento.com/archives/magento/magento-cloud-configuration/magento-magento-cloud-configuration-x.x.x.x.zip&#39; URL konnte nicht zugegriffen werden: HTTP/1.1 \[403 Verboten oder 404 Nicht gefunden\]&quot;*.

(Klicken Sie in der Projekt-Benutzeroberfläche auf das Symbol „Fehler“, um das Protokoll anzuzeigen.)

<u>Erwartetes Ergebnis</u>

Bereitstellung wurde erfolgreich abgeschlossen.

## Ursache

Der Fehler wird dadurch verursacht, dass die Autorisierungsschlüssel (Zugriffsschlüssel) nicht gültig, nicht angegeben oder nicht korrekt angegeben sind.

Einige der Gründe für die Ungültigkeit von Schlüsseln sind:

* Sie haben die Schlüssel mit Ihrem freigegebenen Konto generiert.
* Ihre Lizenz wurde zuvor aufgrund von Zahlungsschwierigkeiten widerrufen.

>[!NOTE]
>
>Wenn dies auf ein Problem mit der Rechnungsstellung oder einem abgelaufenen Vertrag zurückzuführen ist, wenden Sie sich an Ihr Adobe-Account-Team, um Unterstützung zu erhalten. Nach der Reaktivierung Ihrer Lizenz werden Ihre Support- und Bereitstellungsberechtigungen wiederhergestellt.

## Lösung

Führen Sie die folgenden Schritte aus, um das Problem mit den Autorisierungsschlüsseln zu beheben (weitere Informationen zu den einzelnen Schritten finden Sie in den folgenden Abschnitten):

1. Abrufen der gültigen Autorisierungsschlüssel (überspringen Sie diesen Schritt, wenn Sie sich absolut sicher sind, dass Ihr Schlüssel gültig ist).
1. Fügen Sie den Schlüsselwert in der `env:COMPOSER_AUTH` hinzu (oder stellen Sie sicher, dass der richtige Wert vorhanden ist) und überprüfen Sie, ob die Schlüssel in der Variablen auf Projektebene und Umgebungsebene sowie in der `auth.json`-Datei (falls vorhanden) im Projektstamm konsistent angegeben sind.
1. Aktualisieren oder löschen Sie `auth.json`, um eine einzelne Stelle zu haben, an der der Schlüssel konfiguriert ist, wenn die Werte der Autorisierungsschlüssel nicht angegeben sind oder einen anderen Wert haben.

### 1. Erhalten Sie gültige Autorisierungsschlüssel

Wenn Sie die unter dem freigegebenen Konto erstellten Schlüssel verwendet haben, müssen Sie sich an den Adobe Commerce-Lizenzinhaber wenden, der Ihnen Zugriff gewährt, und ihn auffordern, die Schlüssel für Sie zu generieren.

Wenn Ihre Lizenz zuvor aufgrund von Zahlungsproblemen widerrufen wurde, Sie diese Probleme gelöst haben und Ihre Lizenz erneuert wurde, müssen Sie [die neuen Authentifizierungsschlüssel generieren](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html?lang=de).

### 2. Fügen Sie den Schlüsselwert in die Variable env:COMPOSER\_AUTH ein und überprüfen Sie, ob dieselben Schlüssel in auth.json angegeben sind

Weitere Informationen finden Sie in den Anweisungen und [ Informationen unter „Vorhandenes System vorbereiten](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/project/overview) und [Authentifizierungsschlüssel hinzufügen](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/project/overview) in unserer Entwicklerdokumentation.

### 3. Aktualisieren oder Löschen von auth.json

Im Folgenden finden Sie eine schrittweise Beschreibung zum Aktualisieren Ihrer Autorisierungsschlüssel:

1. Melden Sie sich bei dem Computer an, auf dem sich Ihre Adobe Commerce on Cloud Infrastructure SSH-Schlüssel befinden.
1. Melden Sie sich bei Ihrem Projekt an: `magento-cloud login`
1. Erstellen Sie eine Verzweigung, um den Code zu aktualisieren (im folgenden Beispiel wird der Verzweigungsname `auth` aus der primären Verzweigung erstellt):     `magento-cloud environment:branch auth master`
1. Wechseln Sie in das Stammverzeichnis des Projekts.
1. Optional: Löschen Sie die `auth.json`, wenn Sie es vorziehen, und fahren Sie fort [Schritt 9](#step9).
1. Öffnen Sie `auth.json` in einem Texteditor.

   ```json
              {
                "http-basic":  {
                    "repo.magento.com": {
                        "username": "<public_key>",
                        "password": "<private_key>"
                        }
                      }
                    }
   ```

1. Fügen Sie die richtigen Authentifizierungsschlüssel hinzu.
1. Speichern Sie Ihre Änderungen und beenden Sie den Texteditor.
1. Übergeben und Zusammenführen Ihrer Änderungen:

   `git add -A`

   `git commit -m "<message>"`

   `git push origin master`
1. Warten Sie, bis das Projekt bereitgestellt wird.
