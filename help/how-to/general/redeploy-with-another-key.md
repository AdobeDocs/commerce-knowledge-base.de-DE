---
title: 'Adobe Commerce in Cloud: Authentifizierungsschlüssel ändern und erneut bereitstellen'
description: Dieser Artikel enthält Anweisungen dazu, wie Sie Adobe Commerce in der Cloud-Infrastruktur mit verschiedenen Authentifizierungsschlüsseln erneut bereitstellen. Beispielsweise könnten Sie die Schlüssel für ein anderes Konto oder Magento Open Sourcen anstelle von Adobe Commerce-Schlüsseln verwendet haben.
exl-id: 47407c81-5c52-406f-812f-6c6b3ca5cafa
feature: Cloud, Deploy
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Adobe Commerce in Cloud: Authentifizierungsschlüssel ändern und erneut bereitstellen

Dieser Artikel enthält Anweisungen dazu, wie Sie Adobe Commerce in der Cloud-Infrastruktur mit verschiedenen Authentifizierungsschlüsseln erneut bereitstellen. Beispielsweise könnten Sie die Schlüssel für ein anderes Konto oder Magento Open Sourcen anstelle von Adobe Commerce-Schlüsseln verwendet haben.

Wenn Sie falsche Schlüssel verwendet haben, schlägt die Bereitstellung fehl. Zum Wiederherstellen müssen Sie das Projekt klonen, die richtigen Schlüssel zu `auth.json` hinzufügen und die Änderung an die primäre Verzweigung pushen.

In diesem Artikel gehen wir davon aus, dass Ihr Projekt nur eine `master` Verzweigung hat (`master` ist die Standardverzweigung beim ersten Erstellen eines Projekts).

So stellen Sie eine erneute Bereitstellung mit den richtigen Authentifizierungsschlüsseln bereit:

1. Melden Sie sich bei dem Computer an, auf dem sich Ihre Adobe Commerce on Cloud Infrastructure SSH-Schlüssel befinden.
1. Melden Sie sich beim Projekt an:

   ```
   magento-cloud login
   ```

1. Erstellen Sie eine Verzweigung, um den Code mit dem Namen `auth` zu aktualisieren:

   ```
   magento-cloud environment:branch auth master
   ```

1. Wechseln Sie in das Stammverzeichnis des Projekts.
1. Öffnen Sie `auth.json` in einem Texteditor.

   ```json
   {
      "http-basic": {
         "repo.magento.com": {
            "username": "<your public key>",
            "password": "<your private key>"
         }
      }
   }
   ```

1. Fügen Sie die richtigen Authentifizierungsschlüssel hinzu.
1. Speichern Sie Ihre Änderungen und beenden Sie den Texteditor.
1. Übergeben und Zusammenführen Ihrer Änderungen.

   ```
   git add -A
   ```

   ```
   git commit -m "<description of change>"
   ```

   ```
   git push origin master
   ```

1. Warten Sie, bis die Bereitstellung abgeschlossen ist.

Meldungen geben an, ob die Bereitstellung erfolgreich war. Sie können eine erfolgreiche Bereitstellung bestätigen, indem Sie zu einer der **Umgebungsrouten** wechseln, die auf Ihrem Bildschirm angezeigt werden.
