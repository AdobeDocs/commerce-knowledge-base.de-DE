---
title: Problem „setup:static-content:deploy„_version.txt ausführen
description: Dieser Artikel enthält eine Fehlerbehebung für den Fehler „deployed_version.txt“ ist nicht schreibbar, wenn der Befehl „setup:static-content:deploy“ manuell ausgeführt wird.
exl-id: 88d8c126-349f-49cd-8f02-2a32e4994521
feature: Deploy, Page Content, SCD
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: d05f97c9-0a96-5792-92cf-f66ce7326e3a
    internal-label: SCD
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%
---
# Problem `setup:static-content:deploy` deploy_version.txt ausführen

Dieser Artikel bietet eine Fehlerbehebung für den Fehler &quot;`deployed_version.txt` ist nicht schreibbar“, wenn der `setup:static-content:deploy`-Befehl manuell ausgeführt wird.

## Problem

Wenn Sie die Empfehlungen für die Verwendung der Konfigurationsverwaltung in Adobe Commerce zur Cloud-Infrastruktur befolgen (und die Generierung statischer Assets in den Build-Schritt verschieben, um Website-Ausfallzeiten während der Bereitstellung zu reduzieren), tritt möglicherweise der folgende Fehler auf, wenn Sie den `setup:static-content:deploy`-Befehl manuell ausführen:

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
