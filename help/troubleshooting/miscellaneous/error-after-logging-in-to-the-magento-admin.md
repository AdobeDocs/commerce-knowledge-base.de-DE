---
title: Fehler nach der Anmeldung beim Commerce-Administrator
description: Dieser Artikel bietet eine Lösung für den Fall, dass Sie eine Fehlermeldung erhalten, die besagt, dass die angeforderte URL auf diesem Server nicht gefunden wurde.
exl-id: f52b383b-87f2-4216-9bf4-e765db31ca6b
feature: Admin Workspace
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---

# Fehler nach der Anmeldung beim Commerce-Administrator

Dieser Artikel bietet eine Lösung für den Fall, dass Sie eine Fehlermeldung erhalten, die besagt, dass die angeforderte URL auf diesem Server nicht gefunden wurde.

## Details

Die angeforderte URL /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/ wurde auf diesem Server nicht gefunden.

Beachten Sie, dass in der URL kein Schrägstrich zwischen `magento2` und `index.php` vorhanden ist.

## Lösung

Die Basis-URL ist falsch. Die Basis-URL muss:

* Mit `http://` oder `https://` beginnen
* Mit einem Schrägstrich ( `/` ) enden
* Groß-/Kleinschreibung des `web/unsecure/base_url` Datensatzes in der `core_config_data` Datenbanktabelle berücksichtigen

Führen Sie die Installation mit einem gültigen Wert erneut aus.

## Verwandtes Lesen

[Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/de/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook
