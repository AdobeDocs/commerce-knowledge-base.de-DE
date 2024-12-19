---
title: Die Neubereitstellung der Umgebung ist fehlgeschlagen oder der MySQL-Server ist verschwunden.
description: Dieser Artikel bietet eine Lösung für Adobe Commerce-Probleme (alle Bereitstellungsmethoden), bei denen der Ausfall des für MySQL zugewiesenen Speicherplatzes zu stecken gebliebenen Bereitstellungs- oder Datenbankverbindungsfehlern führt.
exl-id: 2086b45a-0bfe-45cc-bef9-1b6f09ddb70a
feature: Deploy, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Die Neubereitstellung der Umgebung ist fehlgeschlagen oder der MySQL-Server ist verschwunden.

Dieser Artikel bietet eine Lösung für Adobe Commerce-Probleme (alle Bereitstellungsmethoden), bei denen der Ausfall des für MySQL zugewiesenen Speicherplatzes zu stecken gebliebenen Bereitstellungs- oder Datenbankverbindungsfehlern führt.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premise und Adobe Commerce on Cloud Infrastructure (alle Versionen)

## Problem

* Der Bereitstellungsprozess schlägt mit dem folgenden Fehler im Bereitstellungsprotokoll (Befehlszeile und Benutzeroberflächenprotokoll) fehl: ```bash    Re-deploying environment abcdefghijklm-master-7rqtwti         E: Environment redeployment failed    ```
* Adobe Commerce antwortet mit dem Fehler 503, und die folgende Fehlermeldung wird in den Anwendungsprotokollen angezeigt:    ```bash    SQLSTATE[HY000] [2006] MySQL server has gone away    ```    und der folgende Fehler erscheint, wenn Sie eine Verbindung zu einem MySQL-Server herstellen:    ```bash    ERROR 2013 (HY000): Lost connection to MySQL server at 'reading initial communication packet', system error: 0 "Internal error/check (Not system error)"    ```

## Ursache

Die wahrscheinlichste Ursache der Probleme ist, dass der zugewiesene Speicherplatz in der MySQL-Datenbank zu niedrig ist. Um dies sicherzustellen, überprüfen Sie den für MySQL verfügbaren Speicherplatz, wie weiter beschrieben.

### Überprüfen, ob genügend Speicherplatz für MySQL vorhanden ist

Für alle Adobe Commerce auf Cloud-Infrastruktur-Starter-Planarchitekturumgebungen und [Integrationsumgebung](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) der Adobe Commerce auf Cloud-Infrastruktur-Pro-Planarchitektur [SSH auf die Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) und führen Sie den Befehl aus:

```bash
magento-cloud db:size
```

Für die Staging- oder Produktionsumgebung der Pro-Architektur [SSH zur Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) und führen Sie die `df -h` aus   Befehl `| grep mysql`. Das Ergebnis sieht in etwa wie folgt aus:

```bash
sxpe7gigd5ok2@i-00baa9e24f31dba41:~$ df -h | grep mysql
/dev/xvdj                            40G  7.4G   32G  19% /data/mysql
```

## Lösung

### Um das Problem zu lösen, müssen Sie mehr Speicherplatz für MySQL zuweisen.

Für alle Starter-Architektur- und Pro-Architektur-Integrationsumgebungen erfolgt dies in der `.magento/services.yaml`-Datei, indem der `mysql: disk:` erhöht wird. Beispiel:

```yaml
mysql:
    type: mysql:10.0
    disk: 2048
```

Siehe den Artikel [Einrichten des MySQL-](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/mysql.html)) als Referenz.

Um diese Änderungen an der Staging- oder Produktionsumgebung der Pro-Architektur vorzunehmen, müssen Sie ein „Support[Ticket erstellen](https://support.magento.com). In der Regel müssen Sie sich jedoch nicht mit dieser Aufgabe in der Staging-/Produktionsumgebung der Pro-Architektur befassen, da Adobe Commerce diese Parameter für Sie überwacht und Sie benachrichtigt und/oder vertragsgemäß Maßnahmen ergreift.

### Anwenden der Änderungen

Nachdem Sie die `.magento/services.yaml` geändert haben, müssen Sie einen Commit ausführen und Ihre Änderungen pushen, damit sie angewendet werden. Mit der Push-Benachrichtigung wird der Bereitstellungsprozess Trigger.
