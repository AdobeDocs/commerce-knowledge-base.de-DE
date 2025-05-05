---
title: Beim Zugriff auf eine neue Integrationsumgebung zur übergeordneten Umgebung umleiten
description: Dieser Artikel enthält Anweisungen zur Fehlerbehebung für das Adobe Commerce-Problem mit der Cloud-Infrastruktur, bei dem der Versuch, auf die neu erstellte Integrationsumgebung zuzugreifen, stattdessen zur übergeordneten Umgebung führt.
exl-id: d1d40c8d-d43c-442e-95c9-76f3cdcafb0e
feature: Cache, Integration, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Beim Zugriff auf eine neue Integrationsumgebung zur übergeordneten Umgebung umleiten

Dieser Artikel enthält Anweisungen zur Fehlerbehebung für das Adobe Commerce-Problem mit der Cloud-Infrastruktur, bei dem der Versuch, auf die neu erstellte Integrationsumgebung zuzugreifen, stattdessen zur übergeordneten Umgebung führt.

Um dies zu beheben, müssen Sie den base\_url-Wert in der Datenbank korrigieren und sicherstellen, dass der `UPDATE_URLS` Variablenwert auf `true` gesetzt ist. Weitere Informationen finden Sie in den folgenden Abschnitten.

Betroffene Versionen und Ausgaben:

* Adobe Commerce auf Cloud-Infrastruktur 2.x.x

## Problem

<u>Schritte zur Reproduktion</u>:

1. Klonen Sie die vorhandene Integrationsverzweigung.
1. Klicken Sie auf die URL für den Zugriff auf die neue Umgebung.

<u>Erwartetes Ergebnis</u>:

Sie gelangen zur neu erstellten Umgebung.

<u>Tatsächliches </u>:

Sie werden zur -Umgebung auf der übergeordneten Verzweigung umgeleitet.

## Lösung

Um das Problem zu beheben, müssen Sie die `base_url` (sicher und unsicher) in der Datenbank der benutzerdefinierten Umgebung korrigieren und die `UPDATE_URL` in der `.magento.env.yaml` festlegen.

### Korrigieren der base\_url-Werte in der Datenbank

Änderungen an der Datenbank können manuell oder über die Adobe Commerce-CLI vorgenommen werden, wenn Sie Version 2.2.0 oder höher verwenden.

#### Die Werte in der DB manuell korrigieren

1. Stellen Sie eine Verbindung zur Datenbank her.
1. Führen Sie die folgenden Befehle aus:

```sql
UPDATE core_config_data SET value = %your_new_environment_unsecure_url% WHERE path="web/unsecure/base_url"
```

```sql
update core_config_data set value = %your_new_environment_secure_url% where path="web/secure/base_url"
```

#### Korrigieren Sie die Datenbank mit Adobe Commerce CLI (verfügbar für Version 2.2.X).

1. Melden Sie sich als [ Adobe Commerce-Dateisystembesitzer an oder wechseln Sie zu diesem](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/web-server/apache.html?lang=de).
1. Führen Sie die folgenden Befehle aus:

```bash
php <your_magento_install_dir>/bin/magento config:set web/unsecure/base_url http://example.com
php <your_magento_install_dir>/bin/magento config:set web/secure/base_url https://example.com
```

### Festlegen der `UPDATE_URLS`

In der lokalen Codebasis im `.magento.env.yaml`:

```
 stage:
    deploy:
        UPDATE_URLS: true
```

### Konfigurations-Cache löschen

Damit die Änderungen angewendet werden, bereinigen Sie den Konfigurations-Cache, indem Sie den folgenden Befehl ausführen:

```bash
php <your_magento_install_dir>/bin/magento cache:clean config
```

## Verwandter Artikel in unserer Entwicklerdokumentation:

[Variablen bereitstellen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=de)
