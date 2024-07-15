---
title: Ausführen des Problems "setup:static-content:deploy" deploy_version.txt
description: Dieser Artikel enthält eine Fehlerbehebung für "deploy_version.txt"ist kein schreibbarer Fehler, wenn der Befehl "setup:static-content:deploy"manuell ausgeführt wird.
exl-id: 88d8c126-349f-49cd-8f02-2a32e4994521
feature: Deploy, Page Content, SCD
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# Problem mit der Ausführung von `setup:static-content:deploy` deploy_version.txt

Dieser Artikel enthält eine Fehlerbehebung für `deployed_version.txt` ist kein schreibbarer Fehler, wenn der Befehl `setup:static-content:deploy` manuell ausgeführt wird.

## Problem

Wenn Sie den Adobe Commerce-Empfehlungen zur Cloud-Infrastruktur folgen, um [Konfigurationsverwaltung](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) zu verwenden (und die Generierung statischer Assets in die Build-Phase verschieben, um die Ausfallzeit von Websites während der Bereitstellung zu verringern), kann beim manuellen Ausführen des Befehls `setup:static-content:deploy` der folgende Fehler auftreten:

```
{{cloud-project-id}}_stg@i:~$ php bin/magento setup:static-content:deploy
Requested languages: en_US
Requested areas: frontend, adminhtml
Requested themes: Magento/blank, Magento/luma, Aheadworks/marketplace, Magento/backend
[Magento\Framework\Exception\FileSystemException]
The path "deployed_version.txt:///app/{{cloud-project-id}}_stg/pub/static/app/{{cloud-project-id}}_stg/pub/static/" is not writable
```

## Ursache

Wir haben den Bereitstellungsprozess optimiert, um Ausfallzeiten zu reduzieren, und Symlinks zu statischen Asset-Dateien erstellt, anstatt sie zu kopieren. Der Speicherort, an dem die statischen Assets gespeichert sind, ist schreibgeschützt. Daher erhalten Sie die oben aufgeführte Fehlermeldung.

Es wird dringend davon abgeraten, die Bereitstellung statischer Inhalte manuell auszuführen, da alle Assets bereits generiert wurden und es keinen Unterschied zwischen Dateien gibt, wenn Sie dies manuell tun (die Designdateien sind ebenfalls schreibgeschützt, Sie können sie nicht ändern). Daher ist ein solcher Vorgang sinnlos.

## Lösung

Wenn Sie weiterhin die Bereitstellung statischer Inhalte ausführen möchten, entfernen Sie symlinks im Verzeichnis `pub/static` und führen Sie den Befehl `setup:static-content:deploy` erneut aus:

```
find pub/static/ -maxdepth 1 -type l -delete
```
