---
title: Klonen des Magento-GitHub-Repositorys nicht möglich
description: Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass Sie das Magento-GitHub-Repository nicht klonen können.
exl-id: 65de77b5-496d-42a3-ab2e-1fff9df97160
feature: Data Import/Export
role: Developer
source-git-commit: 35d4f2130d0ec71f71f5f20aa8a7c76207e7a35a
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 0%

---

# Klonen des Magento-GitHub-Repositorys nicht möglich

Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass Sie das Magento-GitHub-Repository nicht klonen können.

## Detail {#detail}

Der Fehler ähnelt dem folgenden:

```bash
Cloning into 'magento2'...
Permission denied (publickey).
fatal: The remote end hung up unexpectedly
```

## Lösung {#solution}

Laden Sie Ihren SSH-Schlüssel auf GitHub hoch, wie auf [GitHub-Hilfeseite“ beschrieben](https://help.github.com/articles/generating-ssh-keys).
