---
title: "Adobe Commerce on cloud repo konnte nicht aufgerufen werden: Fehler 403 Verboten oder 404 Nicht gefunden bei Bereitstellung"
description: "In diesem Artikel wird erläutert, wie der Adobe Commerce in Bezug auf einen Fehler bei der Bereitstellung von Cloud-Infrastrukturen ähnlich dem folgenden behoben wird:"
exl-id: 2f72d80a-05b2-4908-8fa8-61d06885ed07
feature: Cloud, Deploy, Paas, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---

# Auf Adobe Commerce on Cloud Repo konnte nicht zugegriffen werden: Fehler 403 Verboten oder 404 Nicht gefunden bei Bereitstellung

In diesem Artikel wird beschrieben, wie der Adobe Commerce in Bezug auf einen Fehler bei der Bereitstellung der Cloud-Infrastruktur in etwa wie folgt aufgelöst wird:

&quot;*Auf die URL &quot;https://repo.magento.com/archives/magento/magento-cloud-configuration/magento-magento-cloud-configuration-x.x.x.x.zip&#39;&quot;konnte nicht zugegriffen werden: HTTP/1.1 403 Verboten* &quot;. Oder &quot;*https://repo.magento.com/archives/magento/module-customer-segment/magento-module-customer-segment-102.0.5.0-patch2.zip&quot;konnte nicht heruntergeladen werden (HTTP/1.1 404 Not Found)*&quot;.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x und 2.4.x

## Problem

Fehlermeldung bei der Bereitstellung, die angibt, dass nicht auf die Repo-URL zugegriffen werden konnte.

<u>Zu reproduzierende Schritte</u>

Trigger manuell bereitstellen oder eine Zusammenführung, Push-Benachrichtigung oder Synchronisation Ihrer Umgebung durchführen.

<u>Tatsächliches Ergebnis</u>

Die Implementierung hängt fest. Im Fehlerprotokoll für die Bereitstellung in der Projekt-Benutzeroberfläche wird eine Fehlermeldung ähnlich der folgenden angezeigt:

*&quot;Die &quot;https://repo.magento.com/archives/magento/magento-cloud-configuration/magento-magento-cloud-configuration-x.x.x.x.zip&#39; URL konnte nicht aufgerufen werden: HTTP/1.1 \[403 Verboten oder 404 Nicht gefunden\]&quot;*.

(Klicken Sie in der Projektoberfläche auf das Symbol &quot;Fehler&quot;, um das Protokoll anzuzeigen.)

<u>Erwartetes Ergebnis</u>

Die Implementierung wurde erfolgreich abgeschlossen.

## Ursache

Der Fehler wird dadurch verursacht, dass die Autorisierungsschlüssel (Zugriffsschlüssel) ungültig, nicht angegeben oder nicht korrekt angegeben sind.

Einige der Gründe, warum Schlüssel nicht gültig sind, sind:

* Sie haben die Schlüssel mit Ihrem freigegebenen Konto generiert.
* Ihre Lizenz wurde aufgrund von Zahlungsproblemen bereits widerrufen.

>[!NOTE]
>
>Wenn Sie feststellen, dass dies auf ein Problem mit der Rechnungsstellung oder einem veralteten Vertrag zurückzuführen ist, wenden Sie sich an Ihr Adobe Account-Team, um Ihnen zu helfen, dies zu beheben. Nach der erneuten Aktivierung Ihrer Lizenz werden Ihre Support- und Bereitstellungsberechtigungen wiederhergestellt.

## Lösung

Führen Sie die folgenden Schritte aus, um das Problem mit den Autorisierungsschlüsseln zu beheben (weitere Informationen zu den einzelnen Schritten finden Sie in den folgenden Abschnitten):

1. Ermitteln Sie die gültigen Autorisierungsschlüssel (überspringen Sie diese, wenn Sie sich absolut sicher sind, dass Ihr Schlüssel gültig ist).
1. Fügen Sie den Wert keys in der `env:COMPOSER_AUTH` (oder stellen Sie sicher, dass der richtige Wert vorhanden ist) und überprüfen Sie, ob die Schlüssel konsistent in der Variablen und der `auth.json` im Projektstamm.
1. Aktualisieren oder Löschen `auth.json`, um eine zentrale Stelle zu haben, an der der Schlüssel konfiguriert ist, wenn die Werte der Autorisierungsschlüssel nicht angegeben sind oder einen anderen Wert haben.

### 1. Gültige Zulassungsschlüssel abrufen

Wenn Sie die unter dem freigegebenen Konto erstellten Schlüssel verwendet haben, müssen Sie sich an den Adobe Commerce-Lizenzinhaber wenden, der Ihnen Zugriff gewährt und die Erstellung der Schlüssel anfordert.

Wenn Ihre Lizenz aufgrund von Zahlungsproblemen bereits widerrufen wurde und Sie diese Probleme gelöst haben und Ihre Lizenz erneuert wurde, müssen Sie [neue Authentifizierungsschlüssel generieren](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html).

### 2. Fügen Sie den Schlüsselwert in die Variable env:COMPOSER\_AUTH ein und überprüfen Sie, ob in auth.json dieselben Schlüssel angegeben sind.

Siehe Anweisungen und zugehörige Informationen unter [Vorhandenes System vorbereiten](https://devdocs.magento.com/cloud/setup/first-time-setup-import-prepare.html#auth-json) und [Authentifizierungsschlüssel hinzufügen](https://devdocs.magento.com/cloud/setup/first-time-setup-import-prepare.html#add-authentication-keys) in unserer Entwicklerdokumentation.

### 3. Aktualisieren oder Löschen von auth.json

Im Folgenden wird Schritt für Schritt beschrieben, wie Sie Ihre Autorisierungsschlüssel aktualisieren:

1. Melden Sie sich bei dem Computer an, auf dem Ihre Adobe Commerce auf SSH-Schlüsseln für die Cloud-Infrastruktur installiert ist.
1. Melden Sie sich bei Ihrem Projekt an: `magento-cloud login`
1. Erstellen Sie eine Verzweigung, um den Code zu aktualisieren (im folgenden Beispiel lautet der Zweigname `auth` wird aus der primären Verzweigung erstellt):     `magento-cloud environment:branch auth master`
1. Wechseln Sie zum Stammverzeichnis des Projekts.
1. Optional: Löschen Sie die `auth.json` wenn Sie es vorziehen und fortfahren [Schritt 9](#step9).
1. Öffnen `auth.json` in einem Texteditor.

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
1. Bestätigen Sie Ihre Änderungen und führen Sie sie zusammen:

   `git add -A`

   `git commit -m "<message>"`

   `git push origin master`
1. Warten Sie, bis das Projekt bereitgestellt wurde.
