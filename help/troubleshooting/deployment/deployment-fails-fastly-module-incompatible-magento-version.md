---
title: 'Die Bereitstellung schlägt fehl: Fastly-Modul-kompatible Adobe Commerce-Version'
description: "AKTUALISIERT: 29. Februar 2019"
exl-id: aab77407-94e5-42de-92f4-2f0c19e24fa4
feature: Deploy, Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Die Bereitstellung schlägt fehl: Fastly-Modul-kompatible Adobe Commerce-Version

AKTUALISIERT: 29. Februar 2019

Dieser Artikel enthält eine Korrektur für den Fall, dass die Bereitstellung fehlschlägt, da das Fastly-Modul nicht mit Ihrer aktuellen Adobe Commerce-Version kompatibel ist.

**Problem:** Die Bereitstellung schlägt nach einem neuen Commit und Push fehl, wobei die Fehlermeldung in etwa wie folgt aussieht:

>\[Ausnahme\] Warnung: Fehlendes Argument 3 für Fastly\\Cdn\\Plugin\\.., aufgerufen in /app/vendor/magento/framework/Interception/Interceptor.php ... und definiert in /app/vendor/fastly/magento2/Plugin/ExcludeFilesFromMinification.php ...

**Ursache:** Abwärtskompatible Änderungen im Fastly-Modul v1.2.79.

**Lösung (vorübergehend):** Aktualisieren Sie das Fastly-Modul auf Version 1.2.82 oder höher und laden Sie eine neue VCL in den Commerce Admin hoch. Übertragen Sie dann Ihre Änderungen und übertragen Sie sie auf eine erfolgreiche Implementierung des Triggers.

## Betroffene Versionen

* Adobe Commerce vor Ort 2.1.X
* Adobe Commerce auf Cloud-Infrastruktur 2.1.X
* Fastly-Modul 1.2.79

## Problem

Wenn Sie Ihre Änderungen in die Integration-, Produktions- oder Staging-Umgebung übernehmen und in diese übertragen, löst der nächste Schritt normalerweise den Bereitstellungsprozess aus. Dies geschieht automatisch in Adobe Commerce zur Bearbeitung der Cloud-Infrastruktur und manuell in Adobe Commerce vor Ort.

Die Bereitstellung kann mit den folgenden Fehlermeldungen fehlschlagen:

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

Wenn Sie Adobe Commerce in der Cloud-Infrastrukturlösung verwenden, wird diese Fehlermeldung im [Bereitstellungsprotokoll](https://devdocs.magento.com/guides/v2.3/cloud/trouble/environments-logs.html#log-deploy-log). Bei der lokalen Adobe Commerce-Instanz wird der Fehler in der Befehlszeile angezeigt.

## Ursache

Das Problem wird durch die abwärtskompatiblen Änderungen des Fastly-Moduls v1.2.79 verursacht.

## Lösung

Aktualisieren Sie das Fastly-Modul auf Version 1.2.82 oder höher.

Gehen Sie dazu wie folgt vor:

1. Führen Sie einen der folgenden Befehle aus:
   * wenn das Fastly-Modul in das Magento-cloud-metapaket eingeschlossen ist:    <pre>Composer aktualisiert magento/magento-cloud-metapackage</pre>
   * wenn das Fastly-Modul separat installiert wurde (z. B. wenn Sie Adobe Commerce lokal verwenden, nicht die Cloud-Bearbeitung) <pre>Komponentenaktualisierung schnell/magento2</pre>
1. Übertragen Sie die Änderungen und übernehmen Sie sie per Push-Benachrichtigung. Wenn dies nicht automatisch erfolgt, wird der Bereitstellungsprozess Trigger.
1. Im Admin [Laden Sie die neue VCL auf Fastly hoch](https://devdocs.magento.com/guides/v2.3/cloud/cdn/configure-fastly.html#upload-vcl-snippets).
