---
title: Bereitstellungsfehler, wenn keine Patches gefunden wurden
description: 'Dieser Artikel bietet eine Lösung für das Problem, bei dem ein Fehler angezeigt wird *Die nächsten Patches wurden nicht gefunden: MDVA-XXXXX, ACSD-XXXXX. Bitte überprüfen Sie mit dem Befehl ''status'', ob diese Patches für die aktuelle Magento-Version* verfügbar sind.'
exl-id: 5a2fd35a-892a-48af-a41f-f275297b3e2e
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Bereitstellungsfehler, wenn keine Patches gefunden wurden

Dieser Artikel bietet eine Lösung für das Problem, dass beim Upgrade Ihrer Instanz die Bereitstellung fehlschlägt und ein Fehler in den Bereitstellungsprotokollen angezeigt wird: *Nächste Patches wurden nicht gefunden: MDVA-XXXXX, ACSD-XXXXX. Bitte überprüfen Sie mit dem Befehl „status“ die Verfügbarkeit dieser Patches für die aktuelle Magento-Version*.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, [alle unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).


## Problem

Beim Aktualisieren von Adobe Commerce tritt ein Fehler auf: *Die nächsten Patches wurden nicht gefunden*.

## Ursache

Zuvor angewendete Patches für Ihre ältere(n) Version(en) sind nicht anwendbar oder nicht mehr für Ihre neue Version verfügbar.

## Lösung

1. Überprüfen Sie Ihre `.magento.env.yaml` unter dem Abschnitt QUALITY_PATCH, z. B.

   ```yaml
   QUALITY_PATCHES:
    - MDVA-XXXXX
    - ACSD-XXXXX
   ```

1. Suchen Sie die Patch-IDs in den [Versionshinweisen zu Qualitäts-Patches](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html), um zu überprüfen, ob jede dieser IDs auf die neue Version von Adobe Commerce angewendet werden kann, auf die Sie ein Upgrade durchführen.
1. Wenn der Patch nicht für die neue Version von Adobe Commerce gilt, auf die Sie ein Upgrade durchführen möchten, entfernen Sie die Patch-ID aus der `.magento.env.yaml`.
1. Nachdem Sie alle durch den Fehler angegebenen Patch-IDs überprüft haben, übertragen Sie die Änderungen und stellen Sie sie erneut bereit.

## Verwandtes Lesen

* [Patches anwenden](/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=en#apply-a-patch-in-a-local-environment) in Commerce im Handbuch zur Cloud-Infrastruktur.
