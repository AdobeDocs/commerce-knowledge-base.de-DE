---
title: Anwenden eines Composer-Patches von Adobe
description: In diesem Artikel wird beschrieben, wie Sie einen Composer-Patch für Adobe Commerce On-Premise, Adobe Commerce on Cloud Infrastructure und Magento Open Source anwenden.
exl-id: a9301ad8-1d4b-49f5-b679-758624928219
feature: Cache
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Anwenden eines Composer-Patches von Adobe

In diesem Artikel wird beschrieben, wie Sie einen Composer-Patch für Adobe Commerce On-Premise, Adobe Commerce on Cloud Infrastructure und Magento Open Source anwenden.

>[!WARNING]
>
>Es wird dringend empfohlen, den Patch in der Staging-/Integrationsumgebung anzuwenden und zu testen, bevor er in der Produktion angewendet wird. Wir empfehlen Ihnen auch eine aktuelle Sicherung vor jeder Manipulation.

## Anwenden eines Composer-Patches für Adobe Commerce in der Cloud-Infrastruktur {#cloud}

1. Wenn Sie kein Verzeichnis mit dem Namen `m2-hotfixes` im Projektstammverzeichnis haben, erstellen Sie bitte eines.
1. Kopieren Sie die `%patch_name%.composer.patch` Datei(en) in das `m2-hotfixes`.
1. Code-Änderungen hinzufügen, übertragen und per Push übertragen:

   ```git
   git add -A
   ```

   ```git
   git commit -m "Apply %patch_name%.composer.patch patch"
   ```

   ```git
   git push origin
   ```

Weitere Informationen zum Anwenden von Patches auf Cloud-Projekte finden Sie [Anwenden von Patches](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

### Anwenden eines Composer-Patches für Adobe Commerce On-Premise und Magento Open Source {#commerce}

1. Laden Sie den Patch in Ihr lokales Adobe Commerce- oder Magento Open Source-Stammverzeichnis hoch.
1. Führen Sie den folgenden SSH-Befehl aus:

   ```bash
   patch -p1 < %patch_name%.composer.patch
   ```

   (Wenn der obige Befehl nicht funktioniert, versuchen Sie, `-p2` statt `-p1` zu verwenden.)

1. Damit die Änderungen übernommen werden, aktualisieren Sie den Cache im Admin unter **System** > **Cache-Verwaltung**.
