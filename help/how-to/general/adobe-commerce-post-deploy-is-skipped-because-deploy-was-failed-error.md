---
title: Adobe Commerce *Nach der Bereitstellung wird übersprungen, da die Bereitstellung fehlgeschlagen ist* Fehler
description: "In diesem Artikel wird erläutert, wie ein Bereitstellungsfehler untersucht wird: *Post-deploy wird übersprungen, da die Bereitstellung fehlgeschlagen ist*"
exl-id: cd0a3015-b7b9-442e-8ac1-89447ef12cd7
feature: Deploy
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# Adobe Commerce *Nach der Bereitstellung wird übersprungen, da die Bereitstellung fehlgeschlagen war* Fehler

In diesem Artikel wird erläutert, wie ein Bereitstellungsfehler untersucht wird: *Post-deploy wird übersprungen, da die Bereitstellung fehlgeschlagen war*, was während der Bereitstellung in verschiedenen Umgebungen (z. B. bei der Aktualisierung) auftrat.

## Betroffene Produkte und Versionen

Adobe Commerce in der Cloud-Infrastruktur [alle unterstützten Versionen](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problem

Die Bereitstellung schlägt fehl und gibt eine allgemeine Fehlermeldung zurück, sodass nicht klar ist, wie der Fehler zu beheben ist.

## Ursache

Nicht ermittelt - was diese Fehlermeldung verursacht, hängt vom bereitgestellten Code und der Datenbank ab.

## Ermitteln des Implementierungsfehlers

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

Um die Fehlerverfolgung zur Bestimmung der tatsächlichen Ursache abzurufen, rufen Sie SSH auf den Server auf und überprüfen Sie die Protokolldatei `var/log/install_upgrade.log`.
