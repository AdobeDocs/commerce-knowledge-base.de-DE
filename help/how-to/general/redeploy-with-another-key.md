---
title: 'Adobe Commerce in Cloud: Authentifizierungsschlüssel ändern und erneut bereitstellen'
description: Dieser Artikel enthält Anweisungen dazu, wie Sie Adobe Commerce in der Cloud-Infrastruktur mit verschiedenen Authentifizierungsschlüsseln neu bereitstellen. Beispielsweise könnten Sie die Schlüssel für ein anderes Konto verwendet haben oder Sie haben anstelle von Adobe Commerce-Magento Open Sourcen möglicherweise-Schlüssel verwendet.
exl-id: 47407c81-5c52-406f-812f-6c6b3ca5cafa
feature: Cloud, Deploy
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Adobe Commerce in Cloud: Authentifizierungsschlüssel ändern und erneut bereitstellen

Dieser Artikel enthält Anweisungen dazu, wie Sie Adobe Commerce in der Cloud-Infrastruktur mit verschiedenen Authentifizierungsschlüsseln neu bereitstellen. Beispielsweise könnten Sie die Schlüssel für ein anderes Konto verwendet haben oder Sie haben anstelle von Adobe Commerce-Magento Open Sourcen möglicherweise-Schlüssel verwendet.

Wenn Sie die falschen Schlüssel verwendet haben, schlägt die Bereitstellung fehl. Um das Projekt wiederherzustellen, müssen Sie es klonen, die richtigen Schlüssel zu `auth.json` hinzufügen und die Änderung an die Masterverzweigung übertragen.

In diesem Artikel gehen wir davon aus, dass Ihr Projekt nur über eine `master` -Verzweigung verfügt (`master` ist die Standardverzweigung, wenn Sie zum ersten Mal ein Projekt erstellen).

So stellen Sie die Bereitstellung mit den richtigen Authentifizierungsschlüsseln erneut her:

1. Melden Sie sich bei dem Computer an, auf dem Ihre Adobe Commerce auf SSH-Schlüsseln für die Cloud-Infrastruktur installiert ist.
1. Melden Sie sich beim Projekt an:

   ```
   magento-cloud login
   ```

1. Erstellen Sie eine Verzweigung, um den Code mit dem Namen `auth` zu aktualisieren:

   ```
   magento-cloud environment:branch auth master
   ```

1. Wechseln Sie zum Stammverzeichnis des Projekts.
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
1. Übernehmen Sie Ihre Änderungen und führen Sie sie zusammen.

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

Meldungen geben an, ob die Bereitstellung erfolgreich war. Sie können eine erfolgreiche Bereitstellung bestätigen, indem Sie zu einem der auf Ihrem Bildschirm angezeigten **Umgebungsrouten** navigieren.
