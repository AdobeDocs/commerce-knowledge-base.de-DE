---
title: "'Freigabe fehlgeschlagen: Im Namespace-Fehler 'cache' sind keine Befehle definiert."
description: Dieser Artikel bietet eine Lösung für das Problem, wenn die Bereitstellung mit dem folgenden Fehler fehlschlägt **Im Cache-Namespace sind keine Befehle definiert**.
feature: Deploy
role: Developer
exl-id: ee2bddba-36f7-4aae-87a1-5dbeb80e654e
source-git-commit: 1a8a4e1eada859a6712a43536d7bad26d1ce1244
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# Bereitstellung fehlgeschlagen: Es wurden keine Befehle im Namespace-Fehler &quot;cache&quot;definiert

>[!WARNING]
>
>Sichern Sie zuerst die Datenbank, wenn Sie dies auf einer Live-Produktions-Site tun, bevor Sie diese Schritte durchführen.

Dieser Artikel bietet eine Lösung für das Problem, wenn Ihre Bereitstellung fehlschlägt und einer der Fehler im Protokoll wie folgt aussieht:

```
[YEAR-DAYTIME] ERROR: [127] The command "php ./bin/magento cache:flush --ansi --no-interaction" failed.
        There are no commands defined in the "cache" namespace.
...
      W:     There are no commands defined in the "cache" namespace.
```

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur 2.4.x

## Problem  

<u>Zu reproduzierende Schritte</u>:

Versuchen Sie, sie bereitzustellen. 

<u>Erwartete Ergebnisse</u>:

Sie können die Bereitstellung erfolgreich durchführen.

<u>Tatsächliche Ergebnisse</u>:

Sie werden nicht erfolgreich bereitgestellt. In den Protokollen wird ein Bereitstellungsfehler mit einer Meldung ähnlich der folgenden angezeigt: *Es gibt keine Befehle im Cache-Namespace*.

### Ursache

Die **core_config_data** -Tabelle enthält Konfigurationen für eine Store-ID oder Website-ID, die nicht mehr in der Datenbank vorhanden ist. Dies tritt auf, wenn Sie eine Datenbanksicherung aus einer anderen Instanz/Umgebung importiert haben und die Konfigurationen für diese Bereiche in der Datenbank verbleiben, obwohl die zugehörigen Stores/Websites gelöscht wurden.

### Lösung

Wenn Sie nur eine Website hatten, gilt der zweite Test für die Websites nicht und Sie müssen nur auf Stores testen.

Um dieses Problem zu beheben, identifizieren Sie die ungültigen Zeilen, die aus diesen Konfigurationen übrig bleiben.

1. SSH auf den Server und führen Sie diesen Befehl aus:

   `bin/magento`

1. Die Fehlermeldung kann angeben, welche Zeilen und Tabellen in der Datenbank von gelöschten Sites verbleiben. Beispielsweise gibt der folgende Fehler an, dass der angeforderte Store nicht gefunden wurde:

   ```...
   In StoreRepository.php line 112:
   
   The store that was requested wasn't found. Verify the store and try again.
   ```

1. Führen Sie diese MySql-Abfrage aus, um sicherzustellen, dass der Store nicht gefunden werden kann, was durch die Fehlermeldung in Schritt 2 angegeben wird. 

   ```sql
   select distinct scope_id from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. Führen Sie die folgende MySql-Anweisung aus, um die ungültigen Zeilen zu löschen: 

   ```sql
   delete from core_config_data where scope='stores' and scope_id not in (select store_id from store); 
   ```

1. Führen Sie diesen Befehl erneut aus:

   `bin/magento`

   Wenn Sie einen Fehler wie den folgenden erhalten, der anzeigt, dass die angeforderte Website mit der ID X nicht gefunden wurde, verbleiben Konfigurationen in der Datenbank von Website(en) sowie von gelöschten Stores.

   ```
   In WebsiteRepository.php line 110:
   
   The website with id X that was requested wasn't found. Verify the website and try again.
   ```

   Führen Sie diese MySql-Abfrage aus und überprüfen Sie, ob die Website nicht gefunden werden kann:

   ```sql
   select distinct scope_id from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. Führen Sie diese MySql-Anweisung aus, um die ungültigen Zeilen aus der Website-Konfiguration zu löschen:

   ```sql
   delete from core_config_data where scope='websites' and scope_id not in (select website_id from store_website);
   ```

Um sicherzustellen, dass die Lösung funktioniert hat, führen Sie die `bin/magento` erneut. Sie sollten die Fehler nicht mehr sehen und können sie erfolgreich bereitstellen.

## Verwandtes Lesen

* [Fehlerbehebung bei der Adobe Commerce-Bereitstellung](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-deployment-troubleshooter.html)
* [Überprüfen des Bereitstellungsprotokolls, wenn die Cloud-Benutzeroberfläche den Fehler &quot;Log Snipped&quot; aufweist](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error.html)
