---
title: Adobe Commerce wird nach der Bereitstellung übersprungen, da die Bereitstellung fehlgeschlagen ist. Fehler
description: 'In diesem Artikel wird erläutert, wie Sie einen Bereitstellungsfehler untersuchen: *Nach der Bereitstellung wird übersprungen, da die Bereitstellung fehlgeschlagen ist.*'
exl-id: cd0a3015-b7b9-442e-8ac1-89447ef12cd7
feature: Deploy
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# Adobe Commerce *Nach der Bereitstellung wird übersprungen, da die Bereitstellung fehlgeschlagen ist* Fehler

In diesem Artikel wird erläutert, wie Sie einen Bereitstellungsfehler untersuchen können: *Nach der Bereitstellung wird übersprungen, da die Bereitstellung fehlgeschlagen ist* was bei der Bereitstellung in verschiedenen Umgebungen auftritt, z. B. beim Upgrade.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur [alle unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problem

Die Bereitstellung schlägt fehl und gibt eine allgemeine Fehlermeldung zurück, sodass nicht klar ist, wie der Fehler behoben werden soll.

## Ursache

Unbestimmt : Die Ursache für diese Fehlermeldung hängt vom bereitgestellten Code und der bereitgestellten Datenbank ab.

## Untersuchen des Bereitstellungsfehlers

```
[20XX-XX-XX XX:XX:XX] DEBUG: Running step: is-deploy-failed
    W:
    W: In Processor.php line 129:
    W:
    [20XX-XX-XX XX:XX:XX] ERROR: [201] Post-deploy is skipped because deploy was failed.
    W:   Post-deploy is skipped because deploy was failed.
    W:
    W:
    W: In DeployFailed.php line 39:
    W:
    W:   Post-deploy is skipped because deploy was failed.
    W:
    W:
    W: post-deploy
    W:
```

Um den Fehlertrace zur Bestimmung der eigentlichen Ursache zu erhalten, SSH an den Server senden und die Protokolldatei `var/log/install_upgrade.log` überprüfen.
