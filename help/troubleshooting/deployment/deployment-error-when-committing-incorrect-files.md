---
title: Bereitstellungsfehler bei der Zuweisung falscher Dateien
description: Dieser Artikel bietet eine Lösung für das Problem, wenn Sie Bereitstellungsfehler erhalten, die durch falsche Commits in das Repository von Dateien/Ordnern verursacht werden, die nicht hinzugefügt werden sollten.
feature: Deploy
role: Developer
exl-id: c795f9d5-7171-4846-b99f-c018f1d2bf12
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Bereitstellungsfehler bei der Zuweisung falscher Dateien

In diesem Artikel wird das Problem behoben, das bei Bereitstellungsfehlern auftritt, die durch falsche Commits in das Repository von Dateien/Ordnern verursacht werden, die nicht hinzugefügt werden sollten.

## Betroffene Produkte und Versionen

Adobe Commerce in der Cloud-Infrastruktur (alle Versionen)

## Problem

Sie erhalten Bereitstellungsfehler, wenn Sie eine Übertragung in das Repository von Dateien/Ordnern durchführen. Beispielsweise wird der folgende Fehler durch einen Versuch verursacht, eine Verbindung zur DB herzustellen, wenn diese während der [Build-Phase](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#build-phase) nicht verfügbar ist:

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

Bestimmte Dateien/Ordner sollten nicht in das Repository übertragen werden, da sie einen Umbruch im [Bereitstellungs-Workflow](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html) verursachen.

## Lösung

Entfernen Sie diese Dateien/Ordner aus Ihrem Repository, sofern sie vorhanden sind:

* `app/etc/env.php`
* `pub/media/catalog`
* `vendor`
