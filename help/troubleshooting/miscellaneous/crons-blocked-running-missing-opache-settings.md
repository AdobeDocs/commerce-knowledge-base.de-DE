---
title: 'Cron stoppt aufgrund falsch konfigurierter oder fehlender  [!DNL OpCache] '
description: Dieser Artikel bietet eine Lösung für den Fall, dass Crons aufgrund falsch konfigurierter oder fehlender  [!DNL OpCache]  nicht mehr funktionieren.
exl-id: 30643ea9-969f-41c8-8e62-b24e56d690cf
feature: Cache
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Cron wurde aufgrund falsch konfigurierter oder fehlender [!DNL OpCache] gestoppt

Dieser Artikel bietet eine Lösung für den Fall, dass Cron aufgrund fehlender oder falsch konfigurierter [!DNL OpCache] nicht mehr funktioniert.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur, [alle unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problem

Der Cron hat aufgehört zu funktionieren.

## Ursache

Das [!DNL OpCache] wurde auf eine neuere Version aktualisiert, wodurch ein [!DNL GraphQL]-Plug-in eingeführt wurde, das die `env.php` zur Laufzeit neu schreibt und die Cron-Einstellung überschreiben könnte, was das Problem verursacht haben könnte. Die [!DNL OpCache] muss aktualisiert werden, um Probleme mit dem `env.php file` zu vermeiden. Dies wurde in [Version 2002.1.13](/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package.html?lang=en#v2002.1.13) des [!DNL ECE Tools]-Pakets behoben.

## Lösung

Option 1: Führen Sie im Befehlszeilen-Tool Folgendes aus:

```bash
bin/magento cron:run
```

Es wird möglicherweise eine Meldung angezeigt, dass die Cron-Funktion deaktiviert ist.

Option 2: Öffnen Sie die `app/etc/env.php`-Datei. Wenn Sie das unten sehen, wurde die Cron-Funktion manuell deaktiviert, wurde aufgrund einer fehlgeschlagenen Bereitstellung nicht erneut aktiviert oder das Problem stand im Zusammenhang mit den [!DNL OpCache].

```php
  'cron' =>
  array (
    'enabled' => 0,
  ),
```

1. Wenn die Cron-Funktion deaktiviert ist, führen Sie diesen Befehl aus, um die Cron-Funktion erneut zu aktivieren: `vendor/bin/ece-tools cron:enable`
1. Stellen Sie sicher, dass Sie die neueste Version von [!DNL ECE Tools] verwenden. Falls nicht, führen Sie ein Upgrade durch (oder fahren Sie mit Punkt 3 fort). Führen Sie diesen Befehl aus, um Ihre vorhandene Version zu überprüfen:
   `composer show magento/ece-tools`
1. Wenn Sie bereits die neueste Version von [!DNL ECE Tools] verwenden, überprüfen Sie, ob die `op-exclude.txt` vorhanden ist. Führen Sie dazu diesen Befehl aus:
   `ls op-exclude.txt`.
Wenn diese Datei nicht vorhanden ist, fügen Sie https://github.com/magento/magento-cloud/blob/master/op-exclude.txt zu Ihrem Repository hinzu, übertragen Sie dann die Änderung und stellen Sie sie erneut bereit.
1. Ohne [!DNL ECE Tools] aktualisieren zu müssen, können Sie auch einfach https://github.com/magento/magento-cloud/blob/master/op-exclude.txt in Ihrem Repository hinzufügen/ändern, dann die Änderung übernehmen und erneut bereitstellen.

## Verwandtes Lesen

* [Probleme mit der Cron-Bereitschaftsprüfung](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues.html)
* [Crons-Eigenschaft](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html)
* [Cron-Auftrag steckt im Status „Läuft“ fest](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html)
