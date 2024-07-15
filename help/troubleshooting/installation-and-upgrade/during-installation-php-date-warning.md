---
title: Während der Installation, PHP-Datumswarnung
description: Dieser Artikel enthält eine Fehlerbehebung für eine PHP-Datumswarnung während der Installation.
exl-id: f82c77a9-bbcd-4426-96a0-b3f4b704860b
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '61'
ht-degree: 0%

---

# Während der Installation, PHP-Datumswarnung

Dieser Artikel enthält eine Fehlerbehebung für eine PHP-Datumswarnung während der Installation.

## Details {#details}

Während der Installation wird die folgende Meldung angezeigt:

```text
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more]
```

### Lösung {#solution}

Überprüfen Sie die Einstellung der PHP-Zeitzone sorgfältig. Weitere Informationen finden Sie in unserer Entwicklerdokumentation unter [Installationshandbuch > PHP-Einstellungen](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html) .
