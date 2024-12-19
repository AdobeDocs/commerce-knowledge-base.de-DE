---
title: Bereitstellungsfehler beim Übergeben falscher Dateien
description: Dieser Artikel bietet eine Lösung für das Problem, wenn Sie Bereitstellungsfehler erhalten, die durch falsche Commits in das Repository von Dateien/Ordnern verursacht werden, die nicht hätten hinzugefügt werden sollen.
feature: Deploy
role: Developer
exl-id: c795f9d5-7171-4846-b99f-c018f1d2bf12
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '159'
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
