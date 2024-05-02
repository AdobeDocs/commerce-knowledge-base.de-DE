---
title: Die Neuimplementierung der Umgebung ist fehlgeschlagen oder der MySQL-Server ist weg.
description: Dieser Artikel bietet eine Lösung für Probleme mit Adobe Commerce (alle Bereitstellungsmethoden), bei denen der für MySQL zugewiesene Platzmangel zu blockierten Implementierungs- oder Datenbankverbindungsfehlern führt.
exl-id: 2086b45a-0bfe-45cc-bef9-1b6f09ddb70a
feature: Deploy, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Die Neuimplementierung der Umgebung ist fehlgeschlagen oder der MySQL-Server ist weg.

Dieser Artikel bietet eine Lösung für Probleme mit Adobe Commerce (alle Bereitstellungsmethoden), bei denen der für MySQL zugewiesene Platzmangel zu blockierten Implementierungs- oder Datenbankverbindungsfehlern führt.

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort und Adobe Commerce über Cloud-Infrastruktur (alle Versionen)

## Problem

* Der Bereitstellungsprozess schlägt mit dem folgenden Fehler im Bereitstellungsprotokoll (Befehlszeile und Benutzeroberflächenprotokoll) fehl:  ```bash    Re-deploying environment abcdefghijklm-master-7rqtwti         E: Environment redeployment failed    ```
* Adobe Commerce antwortet mit dem Fehler 503 und die folgende Fehlermeldung wird in den Anwendungsprotokollen angezeigt:    ```bash    SQLSTATE[HY000] [2006] MySQL server has gone away    ```    und der folgende Fehler wird angezeigt, wenn Sie eine Verbindung zu einem MySQL-Server herstellen:    ```bash    ERROR 2013 (HY000): Lost connection to MySQL server at 'reading initial communication packet', system error: 0 "Internal error/check (Not system error)"    ```

## Ursache

Die wahrscheinlichste Ursache für die Probleme ist, dass der MySQL-Datenbank zu wenig Speicherplatz zugewiesen wurde. Um sicherzustellen, dass dies der Fall ist, überprüfen Sie den für MySQL verfügbaren Speicherplatz wie weiter beschrieben.

### Überprüfen Sie, ob für MySQL genügend Platz vorhanden ist.

Für alle Adobe Commerce in den Starter-Planarchitekturumgebungen der Cloud-Infrastruktur und [Integrationsumgebung](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) der Adobe Commerce zur Planarchitektur der Cloud-Infrastruktur Pro [SSH in die Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) und führen Sie den Befehl aus:

```bash
magento-cloud db:size
```

Für die Staging- oder Produktionsumgebung der Pro-Architektur: [SSH in die Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html)und führen Sie die `df -h`   `| grep mysql` Befehl. Das Ergebnis sieht in etwa wie folgt aus:

```bash
sxpe7gigd5ok2@i-00baa9e24f31dba41:~$ df -h | grep mysql
/dev/xvdj                            40G  7.4G   32G  19% /data/mysql
```

## Lösung

### Um das Problem zu lösen, müssen Sie mehr Platz für MySQL bereitstellen.

Für alle Integrationsumgebungen der Starter-Architektur und der Pro-Architektur gilt Folgendes: `.magento/services.yaml` durch Erhöhung der `mysql: disk:` -Parameter. Beispiel:

```yaml
mysql:
    type: mysql:10.0
    disk: 2048
```

Siehe [MySQL-Dienst einrichten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/mysql.html) Artikel als Referenz.

Um diese Änderungen für die Staging- oder Produktionsumgebung der Pro-Architektur vorzunehmen, müssen Sie eine [Support-Ticket](https://support.magento.com). Normalerweise müssen Sie sich aber nicht mit Staging/Produktion der Pro-Architektur befassen, da Adobe Commerce diese Parameter für Sie überwacht und Sie benachrichtigt und/oder vertragsgemäß tätig wird.

### Anwenden der Änderungen

Sobald Sie die `.magento/services.yaml` -Datei, müssen Sie Ihre Änderungen übernehmen und pushen, damit sie angewendet werden. Die Push-Benachrichtigung Trigger den Bereitstellungsprozess.
