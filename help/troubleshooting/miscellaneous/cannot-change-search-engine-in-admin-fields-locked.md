---
title: Suchmaschine in "app/etc/env.php" kann nicht geändert werden
description: Dieser Artikel bietet eine Lösung für das Problem, dass Sie versuchen, die Suchmaschine in Commerce Admin zu ändern, die Felder jedoch gesperrt sind.
exl-id: 61006ce7-34f9-4e4d-a197-f3d627dd277f
source-git-commit: 129e24366aedb132adb84e1f0196d2536422180f
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---

# Suchmaschine in `app/etc/env.php` kann nicht geändert werden

Dieser Artikel bietet eine Lösung für das Problem, dass Sie versuchen, die Suchmaschinenkonfiguration aus der `app/etc/env.php`-Datei zu entfernen, die Konfiguration nach der erneuten Bereitstellung jedoch auf die vorherige Einstellung zurückgesetzt oder standardmäßig auf [!DNL OpenSearch] geändert wird.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, [alle unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problem

Sie versuchen, die Suchmaschine in Commerce Admin zu ändern, aber die Felder sind gesperrt.

## Ursache

Die Suchmaschinenkonfiguration ist in der `app/etc/env.php` gesperrt oder die Suchmaschine wird explizit in der `.magento.env.yaml` definiert.

## Lösung

1. Überprüfen Sie die `.magento.env.yaml` Datei unter der Bereitstellungsphase und überprüfen Sie, ob die `SEARCH_CONFIGURATION` konfiguriert wurde. Beispiel:

   ```yaml
   SEARCH_CONFIGURATION:
     engine: elasticsearch7
     ...
   <VARIABLE X>
   ```

1. Ist die `SEARCH_CONFIGURATION` vorhanden? Wenn nicht vorhanden, ist die Suchmaschinenkonfiguration standardmäßig auf [!DNL OpenSearch] gesperrt. Um die Konfiguration zu ändern, müssen Sie die Variable zur `.magento.env.yaml`-Datei mit dem entsprechenden Wert für die Suchmaschine hinzufügen. Wenn die Variable `SEARCH_CONFIGURATION` vorhanden ist und Sie die Engine ändern möchten, ersetzen Sie den vorhandenen Wert für die Engine in `.magento.env.yaml`. Mögliche/bekannte Werte: [!DNL opensearch], [!DNL livesearch], [!DNL elasticsuite], [!DNL amasty_elastic] und [!DNL amasty_elastic_opensearch].
1. Stellen Sie die Instanz erneut bereit.
1. Das Suchmaschinenfeld in Admin bleibt gesperrt, sollte jedoch mit dem von Ihnen angegebenen Wert aktualisiert werden.

## Verwandtes Lesen

* [Gesperrte (ausgegraute) Felder in Commerce Admin](https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-26879) im Handbuch zu Commerce in der Cloud-Infrastruktur.
