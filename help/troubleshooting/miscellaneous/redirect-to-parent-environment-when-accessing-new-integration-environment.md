---
title: Umleiten zur übergeordneten Umgebung beim Zugriff auf die neue Integrationsumgebung
description: Dieser Artikel enthält Anweisungen zur Fehlerbehebung für die Adobe Commerce zum Problem der Cloud-Infrastruktur, bei dem der Versuch, auf die neu erstellte Integrationsumgebung zuzugreifen, Sie stattdessen zur übergeordneten Umgebung führt.
exl-id: d1d40c8d-d43c-442e-95c9-76f3cdcafb0e
feature: Cache, Integration, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Umleiten zur übergeordneten Umgebung beim Zugriff auf die neue Integrationsumgebung

Dieser Artikel enthält Anweisungen zur Fehlerbehebung für die Adobe Commerce zum Problem der Cloud-Infrastruktur, bei dem der Versuch, auf die neu erstellte Integrationsumgebung zuzugreifen, Sie stattdessen zur übergeordneten Umgebung führt.

Um dies zu beheben, müssen Sie den base\_url -Wert in der Datenbank korrigieren und sicherstellen, dass die Variable `UPDATE_URLS` Variablenwert auf `true`. Weitere Informationen finden Sie in den folgenden Abschnitten.

Betroffene Versionen und Editionen:

* Adobe Commerce auf Cloud-Infrastruktur 2.X.X

## Problem

<u>Zu reproduzierende Schritte</u>:

1. Klonen Sie die vorhandene Integrationsverzweigung.
1. Klicken Sie auf die URL für den Zugriff auf die neue Umgebung.

<u>Erwartetes Ergebnis</u>:

Sie gelangen zur neu erstellten Umgebung.

<u>Tatsächliches Ergebnis</u>:

Sie werden zur Umgebung im übergeordneten Zweig weitergeleitet.

## Lösung

Um das Problem zu beheben, müssen Sie die `base_url` Werte (sicher und unsicher) in der benutzerdefinierten Umgebungsdatenbank und legen Sie die `UPDATE_URL` in der `.magento.env.yaml` -Datei.

### Richtige base\_url-Werte in der Datenbank

Änderungen an der Datenbank können entweder manuell oder über die Adobe Commerce-CLI vorgenommen werden, wenn Sie Version 2.2.0 oder höher verwenden.

#### Manuelles Korrigieren der Werte in der DB

1. Stellen Sie eine Verbindung zur Datenbank her.
1. Führen Sie die folgenden Befehle aus:

```sql
UPDATE core_config_data SET value = %your_new_environment_unsecure_url% WHERE path="web/unsecure/base_url"
```

```sql
update core_config_data set value = %your_new_environment_secure_url% where path="web/secure/base_url"
```

#### Datenbank mithilfe von Adobe Commerce CLI korrigieren (verfügbar für Version 2.2.X)

1. Melden Sie sich bei der [Adobe Commerce-Dateisysteminhaber](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/web-server/apache.html).
1. Führen Sie die folgenden Befehle aus:

```bash
php <your_magento_install_dir>/bin/magento config:set web/unsecure/base_url http://example.com
php <your_magento_install_dir>/bin/magento config:set web/secure/base_url https://example.com
```

### Legen Sie die `UPDATE_URLS` Variable

In Ihrer lokalen Codebase in der `.magento.env.yaml` Dateisatz:

```
 stage:
    deploy:
        UPDATE_URLS: true
```

### Konfigurationscache löschen

Um die Änderungen anzuwenden, leeren Sie den Konfigurationscache, indem Sie den folgenden Befehl ausführen:

```bash
php <your_magento_install_dir>/bin/magento cache:clean config
```

## Verwandter Artikel in unserer Entwicklerdokumentation:

[Bereitstellen von Variablen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html)
