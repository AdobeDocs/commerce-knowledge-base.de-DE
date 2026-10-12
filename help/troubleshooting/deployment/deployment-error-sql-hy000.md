---
title: 'Bereitstellungsfehler: SQLSTATE[HY000]'
description: Dieser Artikel bietet eine Lösung für den Fall, dass die Bereitstellung aufgrund des SQLSTATE[HY000]-Fehlers fehlschlägt.
exl-id: c6da6275-9327-4a5c-99ed-93a53952ba42
feature: Deploy
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 5%
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
