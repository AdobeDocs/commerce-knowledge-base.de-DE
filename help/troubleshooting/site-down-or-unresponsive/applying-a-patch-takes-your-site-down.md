---
title: Durch Anwenden eines Pflasters wird Ihre Website heruntergefahren
description: In diesem Artikel wird über das Problem gesprochen, dass ein Patch, den Sie gerade angewendet haben, Ihre Website herunterfährt. Um es zu beheben, können Sie den Patch entfernen.
exl-id: dc765bcd-0761-4efd-a345-46a908d61272
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Durch Anwenden eines Pflasters wird Ihre Website heruntergefahren

In diesem Artikel wird über das Problem gesprochen, dass ein Patch, den Sie gerade angewendet haben, Ihre Website herunterfährt. Um es zu beheben, können Sie den Patch entfernen.

## Betroffene Produkte und Versionen

* Adobe Commerce (alle Bereitstellungsmethoden), alle unterstützten Versionen
* Magento Open Source, alle Versionen

## Problem

Nachdem Sie einen Patch angewendet haben, geht Ihre Site verloren.

## Ursache

Dieses Problem tritt möglicherweise aufgrund einer Versionsinkompatibilität zwischen dem Patch, den Sie gerade auf Ihre Website angewendet haben, Ihren Anpassungen, anderen Patches, die Sie in der Vergangenheit angewendet haben, oder einem anderen Fehler auf.

## Lösung

Entfernen Sie den Patch. Die Methode zur Patch-Entfernung unterscheidet sich bei Adobe Commerce in der Cloud-Infrastruktur von der in Adobe Commerce vor Ort und Magento Open Source.

### Magento Open Source, alle 1.X-Versionen

Für Magento Open Source 1.x:

* Führen Sie den folgenden SSH-Befehl aus: `h SUPEE_patch --revert `

### Adobe Commerce vor Ort, Magento Open Source, alle 2.x-Versionen

Für Adobe Commerce On-Premise und Magento Open Source 2.x-Versionen:

1. Führen Sie den folgenden SSH-Befehl aus:

   ```
   patch -p1 -R %patch_name%.composer.patch
   ```

   (Wenn der obige Befehl nicht funktioniert, verwenden Sie `-p2` anstelle von `-p1`)

1. Damit die Änderungen übernommen werden, aktualisieren Sie den Cache im Admin unter **System** > **Cache-Verwaltung**.

### Adobe Commerce in der Cloud-Infrastruktur, alle Versionen

Für Adobe Commerce in der Cloud-Infrastruktur werden alle Versionen

1. Entfernen Sie die Datei(en) `%patch_name%.composer.patch` aus dem Verzeichnis `m2-hotfixes` .
1. Übernehmen und pushen Sie Ihre Code-Änderungen:

   ```
   git commit -m "Remove %patch_name%.composer.patch patch" && git push origin
   ```

## Verwandtes Lesen

* [Anwenden eines von Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches in unserer Support-Wissensdatenbank.
