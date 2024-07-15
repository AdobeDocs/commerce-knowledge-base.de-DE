---
title: 'E: Fehler beim Überprüfen von routes.yaml-Fehler während der Staging- oder Produktionsimplementierung'
description: '"Dieser Artikel bietet eine Lösung für das Adobe Commerce-Problem der Cloud-Infrastruktur, bei dem Sie die Fehlermeldung *"E: Error while verifying routes.yaml"* erhalten, wenn Sie versuchen, das Projekt in der Staging- oder Produktionsumgebung bereitzustellen."'
exl-id: 7f58591a-5581-46cd-984d-09ac2c0f3903
feature: Deploy, Routes, Staging
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# E: Fehler beim Überprüfen von routes.yaml-Fehler während der Staging- oder Produktionsimplementierung

Dieser Artikel bietet eine Lösung für das Problem mit der Cloud-Infrastruktur von Adobe Commerce, bei dem Sie die Fehlermeldung &quot;*&quot;E: Error while verifying routes.yaml&quot;*&quot;erhalten, wenn Sie versuchen, das Projekt in der Staging- oder Produktionsumgebung bereitzustellen.

## Betroffene Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle Versionen

## Problem

<u>Zu reproduzierende Schritte</u>:

Trigger einer Bereitstellung durch Pushen des Codes in die Staging- oder Produktionsumgebung.

<u>Erwartetes Verhalten</u>:

Die Implementierung ist erfolgreich.

<u>Tatsächliches Verhalten</u>:

Die Bereitstellung ist blockiert und die folgende Fehlermeldung wird im Protokoll angezeigt:

<pre>Bereitstellen von Anwendungen Überprüfen der Konfiguration E: Fehler beim Überprüfen von routes.yaml.
Die folgenden Domänen sind für Ihren Cluster konfiguriert, haben jedoch keine Routen in Ihrer Datei routes.yaml definiert:

- store1.example.com
- store2.example.com
- test-store.example.com

Mit der aktuellen Konfiguration von routes.yaml
  Diese Domains würden NICHT bedient!

Um fortzufahren, finden Sie hier Anweisungen zur Fehlerbehebung:
 /help/troubleshooting/deployment/e-error-verifying-routes-yaml-error-during-staging-or-production-deploy.md</pre>

## Ursache

Dieser Fehler tritt auf, wenn die Routenkonfiguration für zusätzliche Domänen, die zum Projekt hinzugefügt wurden, in der Datei &quot;`routes.yaml`&quot;fehlt.

Im Rahmen der Adobe Commerce-Selbstdienstaktivierungs-Aktualisierung für die Self-Service-Routenkonfiguration wurde eine Überprüfung vor der Bereitstellung hinzugefügt, um sicherzustellen, dass für alle Domänen in Ihrem Projekt Routen konfiguriert sind, die in der Datei &quot;`routes.yaml`&quot;konfiguriert sind. Wenn bei einer Domain die Routenkonfiguration fehlt, wird die Bereitstellung blockiert.

## Lösung

Um die blockierte Bereitstellung aufzulösen, aktualisieren Sie die Datei &quot;`routes.yaml`&quot;, um Routen für die in der Fehlermeldung aufgeführten Domänen mithilfe einer der folgenden Methoden zu konfigurieren:

* Wenden Sie den von Adobe Commerce während des Aktualisierungsprozesses bereitgestellten Patch an.
* Fügen Sie der Datei `routes.yaml` manuell die fehlende Routenkonfiguration hinzu.

### Methode 1: Wenden Sie das von Adobe Commerce bereitgestellte Patch an.

1. Suchen Sie nach einem kürzlich veröffentlichten Adobe Commerce-Supportticket mit dem Titel &quot;*Self-Service-Funktionen für &lt;project\_ID> aktivieren&quot;*.
1. Befolgen Sie die Anweisungen im Ticket, um den Patch anzuwenden, der die Routenkonfiguration für Ihre Cloud-Umgebung aktualisiert.
1. С Sie die Änderungen an und übertragen Sie sie, um Ihr Projekt erneut bereitzustellen.

### Methode 2: Manuelles Hinzufügen der fehlenden Routenkonfiguration

1. Um alle Domänen in Ihrem Projekt mit derselben Routenkonfiguration bereitzustellen, aktualisieren Sie die Datei &quot;`routes.yaml`&quot;, indem Sie Routenvorlagen für die Standarddomäne und alle anderen Domänen in Ihrem Projekt hinzufügen, wie im folgenden Beispiel gezeigt:

   ```yaml
   "http://{default}/":
       type: upstream
       upstream: "mymagento:http"
   "http://{all}/":
       type: upstream
       upstream: "mymagento:http"
   ```

1. С Sie Ihre Änderungen verschieben und verschieben, um Ihr Projekt erneut bereitzustellen.

Detaillierte Anweisungen zum Aktualisieren der Routenkonfiguration finden Sie unter [Cloud für Adobe Commerce > Routen konfigurieren](https://devdocs.magento.com/guides/v2.3/cloud/project/project-conf-files_routes.html) in unserer Entwicklerdokumentation.

>[!NOTE]
>
>Wenn Ihre Projektkonfiguration Domänen angibt, die nicht mehr verwendet werden, führen Sie die folgenden Schritte aus, um sie so schnell wie möglich aus Ihrem Projekt zu entfernen: 1. Senden Sie ein Support-Ticket mit einer Liste von Domänen, die Sie aus Ihren Projektumgebungen entfernen möchten. 2. Nachdem das Supportteam die Domänen entfernt hat, aktualisieren Sie die Datei &quot;`routes.yaml`&quot;, um alle Verweise auf die veralteten Domänen zu entfernen.
