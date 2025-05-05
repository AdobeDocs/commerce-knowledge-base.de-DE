---
title: 'Bereitstellung bei Cache-Leerung fehlgeschlagen: Fehler „Im Namespace „Cache“ sind keine Befehle definiert.“'
description: Dieser Artikel bietet eine Lösung für das Problem, wenn die Bereitstellung mit dem folgenden Fehler fehlschlägt (** im Cache-Namespace sind keine Befehle definiert**.
feature: Deploy
role: Developer
exl-id: ee2bddba-36f7-4aae-87a1-5dbeb80e654e
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---


# Bereitstellung bei Cache-Leerung fehlgeschlagen: Fehler „Im Namespace &#39;cache&#39; sind keine Befehle definiert.“

>[!WARNING]
>
>Erstellen Sie zunächst eine Sicherungskopie der Datenbank, wenn Sie dies an einer Live-Produktions-Site tun, bevor Sie diese Schritte ausführen.

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

<u>Schritte zur Reproduktion</u>:

Versuchen Sie, bereitzustellen.

<u>Erwartete Ergebnisse</u>:

Sie haben erfolgreich bereitgestellt.

<u>Tatsächliche Ergebnisse</u>:

Die Bereitstellung ist nicht erfolgreich. In den Protokollen wird ein Bereitstellungsfehler mit einer Meldung ähnlich der folgenden angezeigt *Der Cache-Namespace enthält keine Befehle*.

### Ursache

Die **`core_config_data`** enthält Konfigurationen für eine Store-ID oder Website-ID, die nicht mehr in der Datenbank vorhanden ist. Dies tritt auf, wenn Sie eine Datenbanksicherung aus einer anderen Instanz/Umgebung importiert haben und die Konfigurationen für diese Bereiche in der Datenbank verbleiben, obwohl die zugehörigen Stores/Websites gelöscht wurden.

### Lösung

Wenn Sie nur eine Website hatten, dann gilt der zweite Test für die Websites nicht, und Sie müssen nur auf Geschäfte testen.

Um dieses Problem zu beheben, identifizieren Sie die ungültigen Zeilen, die von diesen Konfigurationen übrig bleiben.

1. SSH auf den Server übertragen und diesen Befehl ausführen:

   `bin/magento`

1. Die Fehlermeldung kann anzeigen, welche Zeilen und Tabellen von gelöschten Sites in der Datenbank verbleiben. Im Folgenden finden Sie beispielsweise einen Fehler, der angibt, dass der angeforderte Speicher nicht gefunden wurde:

   ```...
   In StoreRepository.php line 112:
   
   The store that was requested wasn't found. Verify the store and try again.
   ```

1. Führen Sie diese [!DNL MySQL] Abfrage aus, um zu überprüfen, ob der Speicher nicht gefunden werden kann. Dies wird durch die Fehlermeldung in Schritt 2 angezeigt.

   ```sql
   select distinct scope_id from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. Führen Sie die folgende [!DNL MySQL] aus, um die ungültigen Zeilen zu löschen:

   ```sql
   delete from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. Führen Sie diesen Befehl erneut aus:

   `bin/magento`

   Wenn Sie einen Fehler wie den folgenden erhalten, der anzeigt, dass die angeforderte Website mit der ID X nicht gefunden wurde, verbleiben Konfigurationen        in der Datenbank von Websites sowie von Stores, die gelöscht wurden.

   ```
   In WebsiteRepository.php line 110:
   
   The website with id X that was requested wasn't found. Verify the website and try again.
   ```

   Führen Sie diese [!DNL MySQL] Abfrage aus und überprüfen Sie, ob die Website nicht gefunden werden kann:

   ```sql
   select distinct scope_id from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. Führen Sie diese [!DNL MySQL] aus, um die ungültigen Zeilen aus der Website-Konfiguration zu löschen:

   ```sql
   delete from core_config_data where scope='websites' and scope_id not in (select website_id from store_website);
   ```

Um zu bestätigen, dass die Lösung funktioniert, führen Sie den `bin/magento` erneut aus. Die Fehler sollten nicht mehr angezeigt werden und können erfolgreich bereitgestellt werden.

## Verwandtes Lesen

* Fehlerbehebung bei der Bereitstellung von [Adobe Commerce](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-deployment-troubleshooter)
* [Überprüfen des Bereitstellungsprotokolls, wenn in der Cloud-Benutzeroberfläche der Fehler „Protokoll abgeschnitten“ auftritt](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error)
* [Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/de/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook
