---
title: 'Bereitstellungsfehler: SQLSTATE[HY000]'
description: Dieser Artikel bietet eine Lösung für den Fall, dass die Bereitstellung aufgrund des SQLSTATE[HY000]-Fehlers fehlschlägt.
exl-id: c6da6275-9327-4a5c-99ed-93a53952ba42
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---

# Bereitstellungsfehler: SQLSTATE[HY000]

Dieser Artikel bietet eine Lösung für das Problem, dass die Bereitstellung aufgrund des SQLSTATE.[.]-Fehlers fehlschlägt.

## Betroffene Produkte und Versionen

* Adobe Commerce, [alle Bereitstellungsmethoden](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problem

Bei der Bereitstellung tritt ein SQLSTATE-Fehler auf.

```sql
Updating modules:
SQLSTATE[HY000]: General error: 23 Out of resources when opening file '/tmp/#sql_565c_0.MAD' (Errcode: 24 "Too many open files"),
```

## Ursache

Cron wird während der Bereitstellung ausgeführt.

## Lösung

Um das Problem zu beheben, stoppen Sie die Ausführung von Cron, indem Sie die Befehlszeile öffnen und den folgenden Befehl ausführen:
`./vendor/bin/ece-tools cron:disable`.
