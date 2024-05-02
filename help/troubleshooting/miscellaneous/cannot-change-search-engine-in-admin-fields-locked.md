---
title: Suchmaschine in "app/etc/env.php"kann nicht geändert werden.
description: Dieser Artikel bietet eine Lösung für das Problem, dass Sie versuchen, die Suchmaschine in der Commerce-Admin zu ändern, aber die Felder gesperrt sind.
exl-id: 61006ce7-34f9-4e4d-a197-f3d627dd277f
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# Suchmaschine in kann nicht geändert werden `app/etc/env.php`

Dieser Artikel bietet eine Lösung für das Problem, bei dem Sie versuchen, die Suchmaschinenkonfiguration aus dem `app/etc/env.php` -Datei, aber nach der erneuten Bereitstellung wird die Konfiguration auf die vorherige Einstellung zurückgesetzt oder in [!DNL OpenSearch] Standardmäßig.

## Betroffene Produkte und Versionen

* Adobe Commerce zur Cloud-Infrastruktur, [alle unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problem

Sie versuchen, die Suchmaschine in der Commerce-Admin-Instanz zu ändern, aber die Felder sind gesperrt.

## Ursache

Die Suchmaschinenkonfiguration ist in der Variablen `app/etc/env.php` oder die Suchmaschine explizit im `.magento.env.yaml` -Datei.

## Lösung

1. Überprüfen Sie die `.magento.env.yaml` -Datei unter der Bereitstellungsphase und überprüfen Sie, ob die `SEARCH_CONFIGURATION` wurde konfiguriert. Beispiel:

   ```yaml
   SEARCH_CONFIGURATION:
     engine: elasticsearch7
     ...
   <VARIABLE X>
   ```

1. Ist die  `SEARCH_CONFIGURATION` vorhanden? Falls nicht vorhanden, ist die Suchmaschinenkonfiguration auf [!DNL OpenSearch] Standardmäßig. Um die Konfiguration zu ändern, müssen Sie die Variable zum `.magento.env.yaml` -Datei mit dem entsprechenden Wert für die Suchmaschine. Wenn die Variable `SEARCH_CONFIGURATION` vorhanden ist und Sie die Engine ändern möchten, ersetzen Sie den vorhandenen Wert für die Engine in `.magento.env.yaml`. Mögliche/bekannte Werte: [!DNL opensearch], [!DNL livesearch], [!DNL elasticsuite], [!DNL amasty_elastic], und [!DNL amasty_elastic_opensearch].
1. Stellen Sie die Instanz erneut bereit.
1. Das Suchmaschinenfeld im Admin bleibt gesperrt, sollte jedoch mit dem von Ihnen angegebenen Wert aktualisiert werden.

## Verwandtes Lesen

* [Gesperrte Felder in Commerce Admin](/help/troubleshooting/miscellaneous/locked-fields-in-magento-admin.md) in Commerce on Cloud Infrastructure Guide.
