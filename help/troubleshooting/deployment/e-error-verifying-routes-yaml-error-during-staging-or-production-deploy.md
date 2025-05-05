---
title: 'E: Fehler beim Überprüfen von routes.yaml-Fehler während der Staging- oder Produktionsbereitstellung'
description: 'Dieser Artikel bietet eine Lösung für das Adobe Commerce-Problem mit der Cloud-Infrastruktur, bei dem beim Versuch, das Projekt in der Staging- oder Produktionsumgebung bereitzustellen, die Fehlermeldung *„E: Fehler beim Überprüfen von routes.yaml“* angezeigt wird.'
exl-id: 7f58591a-5581-46cd-984d-09ac2c0f3903
feature: Deploy, Routes, Staging
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# E: Fehler beim Überprüfen von routes.yaml-Fehler während der Staging- oder Produktionsbereitstellung

*Dieser Artikel bietet eine Lösung für das Adobe Commerce-Problem mit der Cloud-Infrastruktur, bei dem beim Versuch, das Projekt in der Staging- oder Produktionsumgebung bereitzustellen, die Fehlermeldung „E: Fehler beim Überprüfen* routes.yaml“ angezeigt wird.

## Betroffene Versionen

* Adobe Commerce auf Cloud-Infrastruktur, alle Versionen

## Problem

<u>Schritte zur Reproduktion</u>:

Trigger einer Bereitstellung durch Pushen des Codes in die Staging- oder Produktionsumgebung.

<u>Erwartetes </u>:

Die Bereitstellung war erfolgreich.

<u>Tatsächliches </u>:

Die Bereitstellung ist blockiert und die folgende Fehlermeldung wird im Protokoll angezeigt:

<pre>Anwendungen werden bereitgestellt Konfiguration wird überprüft E: Fehler beim Überprüfen von routes.yaml.
Die folgenden Domains sind für Ihren Cluster konfiguriert, in Ihrer Datei „routes.yaml“ sind jedoch keine Routen definiert:

&#x200B;- store1.example.com
&#x200B;- store2.example.com
&#x200B;- test-store.example.com

Mit Ihrer aktuellen „routes.yaml“-Konfiguration
  diese Domains NICHT bedient werden!

Um fortzufahren, finden Sie hier Anweisungen zur Fehlerbehebung:
 /help/troubleshooting/deployment/e-error-verifying-routes-yaml-error-during-staging-or-production-deploy.md</pre>

## Ursache

Dieser Fehler tritt auf, wenn die Routenkonfiguration für alle zusätzlichen Domains, die Ihrem Projekt hinzugefügt wurden, in der `routes.yaml`-Datei fehlt.

Im Rahmen der Aktualisierung der Adobe Commerce-Self-Service-Aktivierung für die Self-Service-Routenkonfiguration haben wir eine Prüfung vor der Bereitstellung hinzugefügt, um sicherzustellen, dass für alle Domains in Ihrem Projekt Routen in der `routes.yaml` konfiguriert sind. Wenn bei einer Domain die Routenkonfiguration fehlt, wird die Bereitstellung blockiert.

## Lösung

Um die blockierte Bereitstellung zu beheben, aktualisieren Sie die `routes.yaml`-Datei, um Routen für die in der Fehlermeldung aufgelisteten Domains zu konfigurieren, indem Sie eine der folgenden Methoden verwenden:

* Wenden Sie den von Adobe Commerce während des Aktualisierungsprozesses bereitgestellten Patch an.
* Fügen Sie die fehlende Routenkonfiguration manuell zur `routes.yaml` hinzu.

### Methode 1: Wenden Sie das von Adobe Commerce bereitgestellte Patch an

1. Suchen Sie nach einem aktuellen Adobe Commerce-Support-Ticket mit dem Titel &quot;*Self-Service-Funktionen für &lt;project\_ID> aktivieren“.*
1. Befolgen Sie die Anweisungen im Ticket, um den Patch anzuwenden, der die Routenkonfiguration für Ihre Cloud-Umgebung aktualisiert.
1. СÜbergeben und Übertragen der Änderungen, um das Projekt erneut bereitzustellen.

### Methode 2: Manuelles Hinzufügen der fehlenden Routenkonfiguration

1. Um alle Domains in Ihrem Projekt mit derselben Routenkonfiguration zu bedienen, aktualisieren Sie die `routes.yaml`-Datei, indem Sie Routenvorlagen für die Standarddomäne und alle anderen Domains in Ihrem Projekt hinzufügen, wie im folgenden Beispiel gezeigt:

   ```yaml
   "http://{default}/":
       type: upstream
       upstream: "mymagento:http"
   "http://{all}/":
       type: upstream
       upstream: "mymagento:http"
   ```

1. СÜbergeben und Übertragen von Änderungen, um das Projekt erneut bereitzustellen.

Detaillierte Anweisungen zum Aktualisieren der Routenkonfiguration finden Sie unter [Cloud für Adobe Commerce > Routen konfigurieren](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/configure/routes/routes-yaml) in unserer Entwicklerdokumentation.

>[!NOTE]
>
>Wenn Ihre Projektkonfiguration Domänen angibt, die nicht mehr verwendet werden, führen Sie die folgenden Schritte aus, um sie so schnell wie möglich aus Ihrem Projekt zu entfernen: 1. Senden Sie ein Support-Ticket mit einer Liste von Domains, die aus Ihren Projektumgebungen entfernt werden sollen. 2. Nachdem das Support-Team die Domains entfernt hat, aktualisieren Sie die `routes.yaml`-Datei, um alle Verweise auf die veralteten Domains zu entfernen.
