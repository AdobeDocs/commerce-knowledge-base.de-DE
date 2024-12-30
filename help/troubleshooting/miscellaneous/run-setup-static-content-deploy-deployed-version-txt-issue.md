---
title: Problem „setup:static-content:deploy„_version.txt ausführen
description: Dieser Artikel enthält eine Fehlerbehebung für den Fehler „deployed_version.txt“ ist nicht schreibbar, wenn der Befehl „setup:static-content:deploy“ manuell ausgeführt wird.
exl-id: 88d8c126-349f-49cd-8f02-2a32e4994521
feature: Deploy, Page Content, SCD
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# Problem `setup:static-content:deploy` deploy_version.txt ausführen

Dieser Artikel bietet eine Fehlerbehebung für den Fehler &quot;`deployed_version.txt` ist nicht schreibbar“, wenn der `setup:static-content:deploy`-Befehl manuell ausgeführt wird.

## Problem

Wenn Sie die Empfehlungen für die Verwendung der [Konfigurationsverwaltung“ von Adobe Commerce in der Cloud](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md)Infrastruktur befolgen (und die Generierung statischer Assets in die Build-Phase verschieben, um Website-Ausfallzeiten während der Bereitstellung zu reduzieren), tritt möglicherweise die folgende Fehlermeldung auf, wenn Sie den `setup:static-content:deploy`-Befehl manuell ausführen:

```
{{cloud-project-id}}_stg@i:~$ php bin/magento setup:static-content:deploy
Requested languages: en_US
Requested areas: frontend, adminhtml
Requested themes: Magento/blank, Magento/luma, Aheadworks/marketplace, Magento/backend
[Magento\Framework\Exception\FileSystemException]
The path "deployed_version.txt:///app/{{cloud-project-id}}_stg/pub/static/app/{{cloud-project-id}}_stg/pub/static/" is not writable
```

## Ursache

Wir haben den Bereitstellungsprozess optimiert, um Ausfallzeiten zu reduzieren, und haben Symlinks zu statischen Asset-Dateien erstellt, anstatt sie zu kopieren. Der Speicherort der statischen Assets ist schreibgeschützt. Daher wird die obige Fehlermeldung angezeigt.

Es wird dringend empfohlen, die Bereitstellung statischer Inhalte nicht manuell durchzuführen, da alle Assets bereits generiert wurden und es bei manueller Ausführung keinen Unterschied zwischen den Dateien gibt (die Design-Dateien sind ebenfalls schreibgeschützt, Sie können sie nicht ändern). Daher ist ein solcher Vorgang nicht sinnvoll.

## Lösung

Wenn Sie die Bereitstellung statischer Inhalte dennoch ausführen möchten, entfernen Sie Symlinks im `pub/static` und führen Sie den `setup:static-content:deploy` Befehl erneut aus:

```
find pub/static/ -maxdepth 1 -type l -delete
```
