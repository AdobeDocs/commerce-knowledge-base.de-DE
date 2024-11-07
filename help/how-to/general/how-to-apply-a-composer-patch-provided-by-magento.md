---
title: Anwenden eines von Adobe bereitgestellten Composer-Patches
description: In diesem Artikel wird beschrieben, wie Sie einen Composer-Patch für Adobe Commerce vor Ort, Adobe Commerce auf Cloud-Infrastruktur und Magento Open Source anwenden.
exl-id: a9301ad8-1d4b-49f5-b679-758624928219
feature: Cache
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Anwenden eines von Adobe bereitgestellten Composer-Patches

In diesem Artikel wird beschrieben, wie Sie einen Composer-Patch für Adobe Commerce vor Ort, Adobe Commerce auf Cloud-Infrastruktur und Magento Open Source anwenden.

>[!WARNING]
>
>Wir empfehlen dringend, den Patch auf die Staging-/Integrationsumgebung anzuwenden und zu testen, bevor er auf die Produktion angewendet wird. Es wird außerdem empfohlen, vor allen Manipulationen eine Sicherungskopie zu erstellen.

## Anwenden eines Composer-Patches für Adobe Commerce auf die Cloud-Infrastruktur {#cloud}

1. Wenn Sie keinen Ordner mit dem Namen `m2-hotfixes` im Projektstamm haben, erstellen Sie einen.
1. Kopieren Sie die Datei(en) `%patch_name%.composer.patch` in das Verzeichnis `m2-hotfixes` .
1. Fügen Sie Code-Änderungen hinzu, übertragen Sie sie und fügen Sie sie per Push hinzu:

   ```git
   git add -A
   ```

   ```git
   git commit -m "Apply %patch_name%.composer.patch patch"
   ```

   ```git
   git push origin
   ```

Weitere Informationen zum Anwenden von Patches auf Cloud-Projekte finden Sie unter [Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

### Anwenden eines Composer-Patches für Adobe Commerce vor Ort und Magento Open Source {#commerce}

1. Laden Sie den Patch in das Stammverzeichnis der Magento Open Source oder des Adobe Commerce-Ordners hoch.
1. Führen Sie den folgenden SSH-Befehl aus:

   ```bash
   patch -p1 < %patch_name%.composer.patch
   ```

   (Wenn der obige Befehl nicht funktioniert, verwenden Sie `-p2` anstelle von `-p1` )

1. Damit die Änderungen übernommen werden, aktualisieren Sie den Cache im Admin unter **System** > **Cache-Verwaltung**.
