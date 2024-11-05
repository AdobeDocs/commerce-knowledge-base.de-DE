---
title: '"Bereitstellung fehlgeschlagen beim Cache-Leeren: ''Es gibt keine Befehle, die im ''cache''-Namespace''-Fehler definiert sind.'''
description: Dieser Artikel bietet eine Lösung für das Problem, wenn die Bereitstellung mit dem folgenden Fehler fehlschlägt **Im Cache-Namespace sind keine Befehle definiert**.
feature: Deploy
role: Developer
exl-id: ee2bddba-36f7-4aae-87a1-5dbeb80e654e
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---


# Die Bereitstellung ist beim Cache-Leeren fehlgeschlagen: Fehler &quot;Es sind keine Befehle im &#39;cache&#39;-Namespace definiert&quot;

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

Sie werden nicht erfolgreich bereitgestellt. In den Protokollen wird ein Bereitstellungsfehler mit einer Meldung ähnlich der folgenden *Es gibt keine Befehle im Cache-Namespace*.

### Ursache

Die Tabelle **`core_config_data`** enthält Konfigurationen für eine Store-ID oder Website-ID, die nicht mehr in der Datenbank vorhanden ist. Dies tritt auf, wenn Sie eine Datenbanksicherung aus einer anderen Instanz/Umgebung importiert haben und die Konfigurationen für diese Bereiche in der Datenbank verbleiben, obwohl die zugehörigen Stores/Websites gelöscht wurden.

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

1. Führen Sie diese [!DNL MySQL] -Abfrage aus, um zu überprüfen, ob der Store nicht gefunden werden kann, was durch die Fehlermeldung in Schritt 2 angegeben wird.

   ```sql
   select distinct scope_id from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. Führen Sie die folgende [!DNL MySQL] -Anweisung aus, um die ungültigen Zeilen zu löschen:

   ```sql
   delete from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. Führen Sie diesen Befehl erneut aus:

   `bin/magento`

   Wenn Sie einen Fehler wie den folgenden erhalten, der anzeigt, dass die angeforderte Website mit der ID X nicht gefunden wurde, verbleiben Konfigurationen        in der Datenbank von der/den Website(s) sowie von den/den Stores, die gelöscht wurden.

   ```
   In WebsiteRepository.php line 110:
   
   The website with id X that was requested wasn't found. Verify the website and try again.
   ```

   Führen Sie diese [!DNL MySQL] -Abfrage aus und vergewissern Sie sich, dass die Website nicht gefunden werden kann:

   ```sql
   select distinct scope_id from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. Führen Sie diese [!DNL MySQL] -Anweisung aus, um die ungültigen Zeilen aus der Website-Konfiguration zu löschen:

   ```sql
   delete from core_config_data where scope='websites' and scope_id not in (select website_id from store_website);
   ```

Um sicherzustellen, dass die Lösung funktioniert hat, führen Sie den Befehl `bin/magento` erneut aus. Sie sollten die Fehler nicht mehr sehen und können sie erfolgreich bereitstellen.

## Verwandtes Lesen

* [Fehlerbehebung bei der Adobe Commerce-Bereitstellung](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-deployment-troubleshooter)
* [Überprüfen des Bereitstellungsprotokolls, wenn die Cloud-Benutzeroberfläche den Fehler &quot;log snipped&quot;(Protokollausschnitt) aufweist](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error)
* [Best Practices für die Änderung von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Playbook für die Commerce-Implementierung
