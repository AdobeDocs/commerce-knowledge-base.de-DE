---
title: Durch das Anwenden eines Patches wird Ihre Site heruntergefahren
description: In diesem Artikel wird über das Problem gesprochen, dass ein soeben von Ihnen angewendeter Patch Ihre Website herunterfährt. Um dies zu beheben, können Sie den Patch entfernen.
exl-id: dc765bcd-0761-4efd-a345-46a908d61272
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Durch das Anwenden eines Patches wird Ihre Site heruntergefahren

In diesem Artikel wird über das Problem gesprochen, dass ein soeben von Ihnen angewendeter Patch Ihre Website herunterfährt. Um dies zu beheben, können Sie den Patch entfernen.

## Betroffene Produkte und Versionen

* Adobe Commerce (alle Bereitstellungsmethoden), alle unterstützten Versionen
* Magento Open Source, alle Versionen

## Problem

Nachdem Sie ein Pflaster aufgeklebt haben, wird Ihre Site heruntergefahren.

## Ursache

Dieses Problem kann durch eine Versionsinkompatibilität zwischen dem soeben auf Ihrer Website angewendeten Patch, Ihren Anpassungen, anderen in der Vergangenheit angewendeten Patches oder durch einen anderen Fehler verursacht werden.

## Lösung

Entfernen Sie das Pflaster. Die Methode zum Entfernen von Patches unterscheidet sich für Adobe Commerce in der Cloud-Infrastruktur von der für Adobe Commerce On-Premise und Magento Open Source.

### Magento Open Source, alle 1.x-Versionen

Für Magento Open Source 1.x-Versionen

* Führen Sie den folgenden SSH-Befehl aus: `h SUPEE_patch --revert `

### Adobe Commerce On-Premise, Magento Open Source, alle 2.x-Versionen

Für lokale Adobe Commerce-Versionen und Magento Open Source 2.x

1. Führen Sie den folgenden SSH-Befehl aus:

   ```
   patch -p1 -R %patch_name%.composer.patch
   ```

   (Wenn der obige Befehl nicht funktioniert, versuchen Sie, `-p2` statt `-p1` zu verwenden.)

1. Damit die Änderungen übernommen werden, aktualisieren Sie den Cache im Admin unter **System** > **Cache-Verwaltung**.

### Adobe Commerce auf Cloud-Infrastruktur, alle Versionen

Für Adobe Commerce in der Cloud-Infrastruktur: alle Versionen,

1. Entfernen Sie die `%patch_name%.composer.patch` Datei(en) aus dem `m2-hotfixes`.
1. Code-Änderungen übertragen und übertragen:

   ```
   git commit -m "Remove %patch_name%.composer.patch patch" && git push origin
   ```

## Verwandtes Lesen

* [So wenden Sie einen Composer-Patch von Adobe an](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in unserer Support-Wissensdatenbank.
