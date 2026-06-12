---
title: 'Patch: Fehler bei Bereitstellung oder manueller Anwendung nicht gefunden'
description: 'Dieser Artikel bietet eine Lösung für das Problem, bei dem ein Fehler angezeigt wird *Die nächsten Patches wurden nicht gefunden: MDVA-XXXXX, ACSD-XXXXX. Überprüfen Sie die Verfügbarkeit dieser Patches für die aktuelle Version von Magento mithilfe des Befehls ''status''*.'
exl-id: 5a2fd35a-892a-48af-a41f-f275297b3e2e
source-git-commit: 180f0e00ec1a2c6c3bd2ebca4dafe387c7bb3852
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# Patch: Fehler bei Bereitstellung oder manueller Anwendung nicht gefunden

Dieser Artikel bietet eine Lösung für das Problem, dass beim Upgrade Ihrer Instanz die Bereitstellung fehlschlägt und ein Fehler in den Bereitstellungsprotokollen angezeigt wird: *Nächste Patches wurden nicht gefunden: MDVA-XXXXX, ACSD-XXXXX. Überprüfen Sie mithilfe des Befehls „status“, ob diese Patches für die aktuelle Version von Magento verfügbar*.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, [alle unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problem

Beim Aktualisieren von Adobe Commerce tritt ein Fehler auf: *Die nächsten Patches wurden nicht gefunden*.

## Ursache

Zuvor angewendete Patches für Ihre ältere(n) Version(en) sind nicht anwendbar oder nicht mehr für Ihre neue Version verfügbar.

Dieses Problem kann auch auftreten, wenn das installierte Quality Patches Tool-Paket (`magento/quality-patches`) veraltet ist.

Beispiel:

Fall 1:
* Ein Patch könnte ursprünglich für 2.4.7-p9 in QPT 1.1.71 verfügbar gewesen sein
* Eine neuere QPT-Version (z. B. 1.1.72) kann später Unterstützung für 2.4.7-p10 hinzufügen
* Wenn der Kunde Commerce auf 2.4.7-p10 aktualisiert, aber eine ältere QPT-Version installiert lässt, erkennt QPT möglicherweise nicht, dass eine kompatible Patch-Variante für 2.4.7-p10 vorhanden ist

Fall 2:
* In QPT 1.1.72 wurde möglicherweise ein Patch hinzugefügt
* Wenn der Kunde eine ältere QPT-Version installiert lässt, erkennt QPT nicht, dass der Patch vorhanden ist

In diesen Fällen kann die Anwendung des Patches mit einer Meldung wie der folgenden fehlschlagen:

```
Next patches weren't found: ACSD-12345.
Check the availability of these patches for the  current Magento version using the "status" command.
```

Dies geschieht, weil die installierte QPT-Version die aktuelle Commerce-Version nicht einer entsprechenden Version des Patches zuordnen kann.

## Lösung

Dieses Problem ist nicht auf Bereitstellungen beschränkt, die Patches über `.magento.env.yaml` anwenden. Dasselbe zugrunde liegende Problem kann auch auftreten, wenn ein Patch manuell mit folgenden Elementen angewendet wird:

```bash
vendor/bin/magento-patches apply <PATCH_ID>
```

Beispiel:

```
Next patches weren't found: ACSD-12345
Check the availability of these patches for the  current Magento version using the "status" command.
```

In diesem Fall ist der Patch nicht für die Adobe Commerce-Version verfügbar, die in der Umgebung installiert ist, in der der Befehl ausgeführt wird.

1. Überprüfen Sie Ihre `.magento.env.yaml`-Datei unter dem Abschnitt QUALITY_PATCHES , z. B.

   ```yaml
   QUALITY_PATCHES:
    * MDVA-XXXXX
    * ACSD-XXXXX
   ```

1. Suchen Sie die Patch-IDs in den [Versionshinweisen zu Qualitäts-Patches](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/release-notes.html?lang=de), um zu überprüfen, ob jede dieser IDs auf die neue Version von Adobe Commerce angewendet werden kann, auf die Sie ein Upgrade durchführen.
1. Wenn der Patch nicht für die neue Version von Adobe Commerce gilt, auf die Sie ein Upgrade durchführen möchten, entfernen Sie die Patch-ID aus der `.magento.env.yaml`.
1. Nachdem Sie alle durch den Fehler angegebenen Patch-IDs überprüft haben, übertragen Sie die Änderungen und stellen Sie sie erneut bereit.

## Verwandtes Lesen

* [Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de#apply-a-patch-in-a-local-environment) in Commerce im Handbuch zur Cloud-Infrastruktur.
