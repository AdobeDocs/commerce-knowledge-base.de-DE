---
title: Fehler nach der Anmeldung beim Commerce-Administrator
description: Dieser Artikel bietet eine Lösung für das Problem, bei dem Sie eine Fehlermeldung erhalten, dass die angeforderte URL auf diesem Server nicht gefunden wurde.
exl-id: f52b383b-87f2-4216-9bf4-e765db31ca6b
feature: Admin Workspace
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Fehler nach der Anmeldung beim Commerce-Administrator

Dieser Artikel bietet eine Lösung für das Problem, bei dem Sie eine Fehlermeldung erhalten, dass die angeforderte URL auf diesem Server nicht gefunden wurde.

## Details

Die angeforderte URL /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/ wurde auf diesem Server nicht gefunden.

Beachten Sie, dass es in der URL kein Schrägstrich zwischen `magento2` und `index.php` gibt.

## Lösung

Die Basis-URL ist nicht korrekt. Die Basis-URL muss:

* Mit `http://` oder `https://` beginnen
* Mit einem Schrägstrich ( `/` ) enden
* Übereinstimmung mit der Groß-/Kleinschreibung des `web/unsecure/base_url` -Datensatzes in der `core_config_data`-Datenbanktabelle

Führen Sie die Installation mit einem gültigen Wert erneut aus.
