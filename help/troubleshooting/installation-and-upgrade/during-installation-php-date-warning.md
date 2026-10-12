---
title: Während der Installation, PHP-Datumswarnung
description: Dieser Artikel enthält eine Fehlerbehebung für eine PHP-Datumswarnung während der Installation.
exl-id: f82c77a9-bbcd-4426-96a0-b3f4b704860b
feature: Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 1%
---
# Während der Installation, PHP-Datumswarnung

Dieser Artikel enthält eine Fehlerbehebung für eine PHP-Datumswarnung während der Installation.

## Details {#details}

Während der Installation wird die folgende Meldung angezeigt:

```text
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more]
```

### Lösung {#solution}

Überprüfen Sie die Einstellung der PHP-Zeitzone sorgfältig. Siehe [Installationshandbuch > PHP-Einstellungen](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/php-settings) in unserer Entwicklerdokumentation.
