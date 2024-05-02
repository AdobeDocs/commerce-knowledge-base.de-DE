---
title: Große MySQL-Tabellen suchen
description: '"Um die großen Tabellen zu identifizieren, stellen Sie eine Verbindung zur Datenbank her, wie im Artikel [Verbindung zur Datenbank herstellen](https://devdocs.magento.com/cloud/project/project-conf-files_services-mysql.html#connect-to-the-database) beschrieben, und führen Sie den folgenden Befehl aus, wobei "project_id"Ihre Cloud-Projekt-ID ist:"'
exl-id: dc5019bc-ab6c-4568-986f-0a294a0f3ac3
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# Große MySQL-Tabellen suchen

Um die großen Tabellen zu identifizieren, stellen Sie eine Verbindung zur Datenbank her, wie im Abschnitt [Verbindung zur Datenbank herstellen](https://devdocs.magento.com/cloud/project/project-conf-files_services-mysql.html#connect-to-the-database) -Artikel und führen Sie den folgenden Befehl aus, wobei `project_id` ist Ihre Cloud-Projekt-ID:

```sql
SELECT TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "<project_id>"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

Dadurch wird die vollständige Liste der Tabellen und deren Größe angezeigt. Sie können durch die Liste gehen und ermitteln, welche Tabellen aufgrund der großen Größe beachtet werden müssen.
