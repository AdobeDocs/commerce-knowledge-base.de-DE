---
title: Bereitstellungsfehler beim Übergeben falscher Dateien
description: Dieser Artikel bietet eine Lösung für das Problem, wenn Sie Bereitstellungsfehler erhalten, die durch falsche Commits in das Repository von Dateien/Ordnern verursacht werden, die nicht hätten hinzugefügt werden sollen.
feature: Deploy
role: Developer
exl-id: c795f9d5-7171-4846-b99f-c018f1d2bf12
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
source-wordcount: '181'
ht-degree: 0%
---
# Bereitstellungsfehler beim Übergeben falscher Dateien

Dieser Artikel bietet eine Lösung für das Problem, wenn Bereitstellungsfehler auftreten, die durch falsche Übertragungen an das Repository von Dateien/Ordnern verursacht werden, die nicht hätten hinzugefügt werden sollen.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur (alle Versionen)

## Problem

Bereitstellungsfehler treten auf, wenn Sie einen Commit für das Repository mit Dateien/Ordnern ausführen. Beispielsweise wird der folgende Fehler durch den Versuch verursacht, eine Verbindung zur Datenbank herzustellen, wenn diese derzeit während der Build-[ nicht verfügbar ist](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#build-phase):

```SQL
SQLSTATE[HY000] [2002] php_network_getaddresses: getaddrinfo for database.i  
          nternal failed: Name or service not known                                    
                                                                                       
        
        In Abstract.php line 124:
                                                                                       
          SQLSTATE[HY000] [2002] php_network_getaddresses: getaddrinfo for database.i  
          nternal failed: Name or service not known                                    
                                                                                       
        
        In Abstract.php line 124:
                                                                                       
          PDO::__construct(): php_network_getaddresses: getaddrinfo for database.inte  
          rnal failed: Name or service not known       
```

## Ursache

Bestimmte Dateien/Ordner sollten nicht in das Repository übertragen werden, da sie einen Bruch im [Bereitstellungs-Workflow) ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html).

## Lösung

Entfernen Sie diese Dateien/Ordner aus Ihrem Repository, falls sie vorhanden sind:

* `app/etc/env.php`
* `pub/media/catalog`
* `vendor`
