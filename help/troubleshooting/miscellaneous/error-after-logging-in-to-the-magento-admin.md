---
title: Fehler nach der Anmeldung beim Commerce-Administrator
description: Dieser Artikel bietet eine Lösung für den Fall, dass Sie eine Fehlermeldung erhalten, die besagt, dass die angeforderte URL auf diesem Server nicht gefunden wurde.
exl-id: f52b383b-87f2-4216-9bf4-e765db31ca6b
feature: Admin Workspace
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '166'
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

[Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook
