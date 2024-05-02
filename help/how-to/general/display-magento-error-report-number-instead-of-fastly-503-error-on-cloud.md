---
title: Adobe Commerce-Fehlerberichtsnummer anstelle des Fastly 503-Fehlers anzeigen
description: 'Standardmäßig werden alle Adobe Commerce-Fehler schnell hinter dem Fehler **503 Service Nicht verfügbar** verborgen. Um die Berichtsnummer des Adobe Commerce-Fehlerprotokolls anzuzeigen (um ihn in den Protokollen zu finden und die Fehlerdetails anzuzeigen), öffnen Sie die Website, auf der die Schritte weggelassen werden:'
exl-id: c0a4a9f8-a674-4cef-8088-e844594e6076
feature: Cache, Cloud
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Adobe Commerce-Fehlerberichtsnummer anstelle des Fastly 503-Fehlers anzeigen

Standardmäßig werden alle Adobe Commerce-Fehler schnell hinter dem **503 Dienst nicht verfügbar** Fehler. Um die Berichtsnummer des Adobe Commerce-Fehlerprotokolls anzuzeigen (um ihn in den Protokollen zu finden und die Fehlerdetails anzuzeigen), öffnen Sie die Website, auf der Sie den Vorgang ausgelassen haben, indem Sie die folgenden Schritte ausführen:

1. Fügen Sie die Domäne und IP-Adresse Ihrer Anwendung zu Ihrer Hostdatei auf Ihrem lokalen Computer hinzu.
1. Löschen Sie den Browsercache und die Cookies (oder wechseln Sie in den Inkognito-Modus).
1. Öffnen Sie die Website Ihres Stores erneut, um den Adobe Commerce-Fehler zu sehen.

Wenn Sie den echten Adobe Commerce-Fehler und die Fehlerberichtsnummer sehen, erhalten Sie möglicherweise Details in der Fehlerberichtsdatei, indem Sie die folgenden Schritte ausführen:

1. SSH in die betroffene Umgebung. Siehe Abschnitt [SSH in einer Umgebung](https://devdocs.magento.com/guides/v2.3/cloud/env/environments-ssh.html#ssh) in unserer Entwicklerdokumentation.
1. Suchen Sie die `./var/report/{error_number}` -Datei.

## Anwendungsdomäne und IP-Adresse zu Ihrer Hostdatei hinzufügen: detaillierte Schritte

1. Überprüfen Sie die Server-IP Ihres Stores, indem Sie die `nslookup` -Befehl in der Befehlszeile auf Ihrem lokalen Computer:
   * Benutzer der Pro-Architektur (Staging- und Produktionsumgebungen):

   ```
   nslookup {your_project_id}.ent.magento.cloud
   ```

   * Benutzer der Starterarchitektur (alle Umgebungen); Benutzer der Pro-Architektur (Integrationsumgebung):

   ```
   nslookup gw.{your_region}.magentosite.cloud
   ```

1. Fügen Sie Ihre Store-Domäne und die Anwendungs-Server-IP-Adresse der Hostdatei auf Ihrem lokalen Computer im folgenden Format hinzu:

```
{server_IP} {store_domain}
```
