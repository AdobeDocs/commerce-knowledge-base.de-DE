---
title: Bereitstellungsfehler, bei denen keine Patches gefunden wurden
description: "Dieser Artikel bietet eine Lösung für das Problem, dass Sie einen Fehler sehen *Nächste Patches wurden nicht gefunden: MDVA-XXXXX, ACSD-XXXXX. Bitte überprüfen Sie die Verfügbarkeit dieser Patches mit dem Befehl 'status' für die aktuelle Magento-Version*."
exl-id: 5a2fd35a-892a-48af-a41f-f275297b3e2e
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Bereitstellungsfehler, bei denen keine Patches gefunden wurden

Dieser Artikel bietet eine Lösung für das Problem, dass beim Aktualisieren Ihrer Instanz die Bereitstellung fehlschlägt und in den Bereitstellungsprotokollen ein Fehler angezeigt wird: *Die nächsten Patches wurden nicht gefunden: MDVA-XXXXX, ACSD-XXXXX. Bitte überprüfen Sie mit der &quot;status&quot;-Befehlsverfügbarkeit dieser Patches für die aktuelle Magento-Version.*.

## Betroffene Produkte und Versionen

* Adobe Commerce zur Cloud-Infrastruktur, [alle unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).


## Problem

Beim Aktualisieren von Adobe Commerce tritt ein Fehler auf: *Die nächsten Patches wurden nicht gefunden*.

## Ursache

Zuvor angewendete Patches für Ihre älteren Versionen sind für Ihre neue Version nicht verfügbar oder nicht mehr verfügbar.

## Lösung

1. Überprüfen Sie Ihre `.magento.env.yaml` -Datei unter dem Abschnitt QUALITY_PATCH, z. B.

   ```yaml
   QUALITY_PATCHES:
    - MDVA-XXXXX
    - ACSD-XXXXX
   ```

1. Suchen Sie die Patch-IDs im [Versionshinweise zu Qualitätsmustern](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) , um zu überprüfen, ob jede Version auf die neue Version von Adobe Commerce angewendet werden kann, auf die Sie aktualisieren.
1. Wenn der Patch nicht für die neue Version von Adobe Commerce gilt, auf die Sie aktualisieren möchten, entfernen Sie die Patch-ID aus dem `.magento.env.yaml` -Datei.
1. Nachdem Sie alle Patch-IDs geprüft haben, die durch den Fehler gekennzeichnet sind, pushen Sie die Änderungen und stellen Sie sie erneut bereit.

## Verwandtes Lesen

* [Anwenden von Patches](/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=en#apply-a-patch-in-a-local-environment) in Commerce on Cloud Infrastructure Guide.
