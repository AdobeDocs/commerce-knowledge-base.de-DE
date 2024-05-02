---
title: Cron-Haltepunkte aufgrund fehlender Konfiguration [!DNL OpCache] settings
description: Dieser Artikel bietet eine Lösung für den Fall, dass Crons aufgrund einer falsch konfigurierten oder fehlenden Konfiguration nicht mehr funktionieren. [!DNL OpCache] -Einstellungen.
exl-id: 30643ea9-969f-41c8-8e62-b24e56d690cf
feature: Cache
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Cron wurde aufgrund einer Fehlkonfiguration oder Fehlfunktion angehalten [!DNL OpCache] settings

Dieser Artikel bietet eine Lösung für den Fall, dass Cron aufgrund fehlender oder falsch konfigurierter Elemente nicht mehr funktioniert [!DNL OpCache] -Einstellungen.

## Betroffene Produkte und Versionen

Adobe Commerce zur Cloud-Infrastruktur, [alle unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problem

Der Cron funktionierte nicht mehr.

## Ursache

Die [!DNL OpCache] wurde auf eine neuere Version aktualisiert, mit der ein [!DNL GraphQL] Plug-in, das die `env.php` in der -Laufzeitumgebung und die Cron-Einstellung überschreiben könnte, was das Problem verursacht haben könnte. Die [!DNL OpCache] -Konfiguration aktualisiert werden, um Probleme mit der `env.php file`und das in [Version 2002.1.13](/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package.html?lang=en#v2002.1.13) des [!DNL ECE Tools] Paket.

## Lösung

Option 1: Führen Sie im Befehlszeilen-Tool Folgendes aus:

```bash
bin/magento cron:run
```

Eine Meldung kann anzeigen, dass der Cron deaktiviert ist.

Option 2: Öffnen Sie die `app/etc/env.php` -Datei: Wenn Sie die unten stehende Datei sehen, wurde der Cron manuell deaktiviert, aufgrund einer fehlgeschlagenen Bereitstellung nicht erneut aktiviert oder das Problem bezog sich auf die [!DNL OpCache] -Einstellungen.

```php
  'cron' =>
  array (
    'enabled' => 0,
  ),
```

1. Wenn der Cron deaktiviert ist, führen Sie diesen Befehl aus, um den Cron erneut zu aktivieren: `vendor/bin/ece-tools cron:enable`
1. Stellen Sie sicher, dass Sie die neueste Version von [!DNL ECE Tools]. Ist dies nicht der Fall, aktualisieren Sie (oder überspringen Sie auf Artikel 3). Führen Sie folgenden Befehl aus, um Ihre vorhandene Version zu überprüfen:
   `composer show magento/ece-tools`
1. Wenn Sie bereits die neueste Version von [!DNL ECE Tools], überprüfen Sie, ob die `op-exclude.txt` -Datei. Führen Sie dazu folgenden Befehl aus:
   `ls op-exclude.txt`.
Wenn diese Datei nicht vorhanden ist, fügen Sie https://github.com/magento/magento-cloud/blob/master/op-exclude.txt zu Ihrem Repo hinzu, übernehmen Sie die Änderung und stellen Sie sie erneut bereit.
1. Ohne Aktualisierung [!DNL ECE Tools], können Sie auch einfach https://github.com/magento/magento-cloud/blob/master/op-exclude.txt in Ihrem Repo hinzufügen/ändern, dann die Änderung übernehmen und erneut bereitstellen.

## Verwandtes Lesen

* [Probleme bei der Cron-Bereitschaft-Überprüfung](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues.html)
* [Crons-Eigenschaft](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html)
* [Cron-Auftrag bleibt im Status &quot;Wird ausgeführt&quot; stecken](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html)
