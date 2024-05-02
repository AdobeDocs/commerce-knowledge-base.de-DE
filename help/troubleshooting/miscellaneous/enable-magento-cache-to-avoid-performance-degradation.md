---
title: Cache aktivieren, um Leistungsbeeinträchtigungen zu vermeiden
description: In diesem Artikel wird erläutert, wie ein langsames Site-Problem gelöst wird, das durch die Deaktivierung bestimmter Adobe Commerce-Cache-Typen verursacht wird.
exl-id: e4e5a753-efa3-4552-aaf6-28e44efcfa5b
feature: Cache, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# Cache aktivieren, um Leistungsbeeinträchtigungen zu vermeiden

In diesem Artikel wird erläutert, wie ein langsames Site-Problem gelöst wird, das durch die Deaktivierung bestimmter Adobe Commerce-Cache-Typen verursacht wird.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x
* Adobe Commerce lokal 2.2.x, 2.3.x

## Problem

Sie bemerken eine Leistungsbeeinträchtigung. Beispielsweise wird die Checkout-Seite langsam geladen oder der Apdex-Wert in New Relic sinkt.

## Ursache

Ein Grund für die Leistungsbeeinträchtigung kann die Deaktivierung bestimmter Adobe Commerce-Cache-Typen sein.

## Lösung

1. Überprüfen Sie zunächst den Status Ihres Adobe Commerce-Caches, um festzustellen, ob dies das Problem ist. Dazu [SSH in Ihrer Umgebung](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh) und führen Sie den folgenden Befehl aus:

   ```bash
   php bin/magento cache:status
   ```

   Dadurch wird der Status jedes Cache-Typs angezeigt (&quot;0&quot; für deaktiviert, &quot;1&quot; für aktiviert). Sie können diese Informationen auch im Abschnitt `app/etc/env.php` -Datei.

1. Untersuchen Sie die deaktivierten Cache-Typen. Alle Adobe Commerce-Cache-Typen sollten aktiviert sein, es sei denn, Sie erhalten alternative Anleitungen von Adobe. Für Drittanbietererweiterungen ist es nicht erforderlich, den Adobe Commerce-Cache zu deaktivieren.
1. Wenn die Untersuchung bestätigt, dass einige Cache-Typen versehentlich deaktiviert sind, aktivieren Sie sie, indem Sie für jeden Cache-Typ den folgenden Befehl ausführen: `php bin/magento cache:enable <your_disabled_cache_type>`

Wenn es Bedenken und/oder Fragen gibt, ob ein bestimmter Adobe Commerce-Cache-Typ deaktiviert werden kann oder sollte, [Adobe Commerce-Support kontaktieren](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) Empfehlungen einzuholen.

## Verwandtes Lesen

Adobe Commerce-Cache-Dokumentation in unserer Entwicklerdokumentation:

* [Überblick über den Adobe Commerce-Cache](https://devdocs.magento.com/guides/v2.3/frontend-dev-guide/cache_for_frontdevs.html)
* [Verwalten des Cache](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-cache.html)

Andere mögliche Gründe für Leistungsprobleme und Lösungen für diese:

* [Adobe Commerce-Bannerausgabe deaktivieren, um die Site-Leistung zu verbessern](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md)
* [MySQL-Tabellen sind zu groß](/help/troubleshooting/database/mysql-tables-are-too-large.md)
* [Langsame Leistung, langsame und lange laufende Crons](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md)
* [Eingeschränkter Administratorzugriff, der Leistungsprobleme verursacht](/help/troubleshooting/miscellaneous/restricted-admin-access-causing-performance-issues.md)
