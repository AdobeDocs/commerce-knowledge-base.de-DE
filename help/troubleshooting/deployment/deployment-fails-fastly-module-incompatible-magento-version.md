---
title: Bereitstellung schlägt fehl Fastly-Modul inkompatible Adobe Commerce-Version
description: 'AKTUALISIERT: 29. Februar 2019'
exl-id: aab77407-94e5-42de-92f4-2f0c19e24fa4
feature: Deploy, Extensions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Bereitstellung schlägt fehl Fastly-Modul inkompatible Adobe Commerce-Version

AKTUALISIERT: 29. Februar 2019

Dieser Artikel enthält eine Fehlerbehebung für den Fall, dass die Bereitstellung fehlschlägt, da das Fastly-Modul mit Ihrer aktuellen Adobe Commerce-Version inkompatibel ist.

**Problem** Die Bereitstellung schlägt nach einem neuen Commit und einer Push-Benachrichtigung fehl, wobei die Fehlermeldung in etwa wie folgt aussieht:

>\[Exception\] Warnung: Fehlendes Argument 3 für Fastly\\Cdn\\Plugin\\…, aufgerufen in /app/vendor/magento/framework/Interception/Interceptor.php … und definiert in /app/vendor/fastly/magento2/Plugin/ExcludeFilesFromMinification.php …

**Ursache:** rückwärts inkompatible Änderungen im Fastly-Modul v1.2.79.

**Lösung (temporär):** Aktualisieren Sie das Fastly-Modul auf Version 1.2.82 oder höher und laden Sie eine neue VCL in Commerce Admin hoch. Übergeben Sie dann Ihre Änderungen und übertragen Sie sie auf den Trigger einer erfolgreichen Bereitstellung.

## Betroffene Versionen

* Adobe Commerce On-Premises 2.1.x
* Adobe Commerce auf Cloud-Infrastruktur 2.1.x
* Fastly-Modul 1.2.79

## Problem

Wenn Sie einen Commit ausführen und Ihre Änderungen in die Integrations-, Produktions- oder Staging-Umgebung pushen, wird in der Regel der Bereitstellungsprozess durch den nächsten Schritt ausgelöst. Dies geschieht automatisch in Adobe Commerce in der Cloud Infrastructure Edition und manuell in Adobe Commerce On-Premise.

Die Bereitstellung schlägt möglicherweise mit den folgenden Fehlermeldungen fehl:

```
[2019-01-23 00:00:00] INFO: php ./bin/magento setup:static-content:deploy --ansi --no-interaction --jobs 1 --exclude-theme Magento/luma en_GB en_US
[2019-01-23 00:00:00] CRITICAL:
  Requested languages: en_GB, en_US
  Requested areas: frontend, adminhtml
  Requested themes: Magento/blank, Magento/backend
  === frontend -> Magento/blank -> en_GB ===

    [Exception]
    Warning: Missing argument 3 for Fastly\Cdn\Plugin\ExcludeFilesFromMinification::afterGetExcludes(), called in /app/vendor/magento/framework/Interception/Interceptor.php on line 152 and defined in /app/vendor/fastly/magento2/Plugin/ExcludeFilesFromMinification.php on line 38

  setup:static-content:deploy [-d|--dry-run] [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [-t|--theme[="..."]] [--exclude-theme[="..."]] [-l|--language[="..."]] [--exclude-language[="..."]] [-a|--area[="..."]] [--exclude-area[="..."]] [-j|--jobs[="..."]] [--symlink-locale] [languages1] ... [languagesN]

[2019-01-23 000:00:00] INFO: Set flag: var/.deploy_is_failed
[2019-01-23 00:00:00] CRITICAL: Command php ./bin/magento setup:static-content:deploy --ansi --no-interaction --jobs 1 --exclude-theme Magento/luma en_GB en_US returned code 1
```

Wenn Sie Adobe Commerce in einer Cloud-Infrastrukturlösung verwenden, wird diese Fehlermeldung im &quot;[&quot; ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations). Bei On-Premise-Adobe Commerce wird der Fehler in der Befehlszeile angezeigt.

## Ursache

Das Problem wird durch die abwärtsinkompatiblen Änderungen im Fastly-Modul v1.2.79 verursacht.

## Lösung

Aktualisieren Sie das Fastly-Modul auf Version 1.2.82 oder höher.

Gehen Sie dazu wie folgt vor:

1. Führen Sie einen der folgenden Befehle aus:
   * wenn das Fastly-Modul im magento-cloud-metapaket enthalten ist:    <pre>Composer-Update Magento/Magento-Cloud-Metapaket</pre>
   * wenn das Fastly-Modul separat installiert wurde (z. B. wenn Sie Adobe Commerce lokal verwenden, nicht die Cloud-Edition) <pre>Composer Update Fastly/Magento2</pre>
1. Übergeben Sie die Änderungen, übertragen Sie sie und führen Sie einen Trigger des Bereitstellungsprozesses aus, wenn er nicht automatisch durchgeführt wird.
1. Laden Sie in der Admin [die neue VCL in Fastly hoch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#upload-vcl-snippets).
