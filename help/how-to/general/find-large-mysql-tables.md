---
title: Große MySQL-Tabellen suchen
description: 'Um die großen Tabellen zu identifizieren, stellen Sie eine Verbindung zur Datenbank her, wie im Artikel [Verbindung zur Datenbank herstellen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/mysql#connect-to-the-database) beschrieben, und führen Sie den folgenden Befehl aus, wobei "project_id"Ihre Cloud-Projekt-ID ist:'
exl-id: dc5019bc-ab6c-4568-986f-0a294a0f3ac3
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---

# Große MySQL-Tabellen suchen

Um die großen Tabellen zu identifizieren, stellen Sie eine Verbindung zur Datenbank her, wie im Artikel [Verbindung zur Datenbank herstellen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/mysql#connect-to-the-database) beschrieben, und führen Sie den folgenden Befehl aus, wobei `project_id` Ihre Cloud-Projekt-ID ist:

```sql
SELECT TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "<project_id>"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

Dadurch wird die vollständige Liste der Tabellen und deren Größe angezeigt. Sie können durch die Liste gehen und ermitteln, welche Tabellen aufgrund der großen Größe beachtet werden müssen.

## Verwandtes Lesen

[Best Practices für die Änderung von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Playbook für die Commerce-Implementierung
