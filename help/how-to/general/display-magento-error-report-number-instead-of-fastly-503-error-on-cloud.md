---
title: Adobe Commerce-Fehlerberichtnummer anstelle von Fastly 503-Fehler anzeigen
description: 'Standardmäßig werden in Fastly alle Adobe Commerce-Fehler hinter dem Fehler **503 Service Unavailable** ausgeblendet. Um die Nummer des Adobe Commerce-Fehlerprotokollberichts anzuzeigen (um sie in den Protokollen zu finden und die Fehlerdetails anzuzeigen), öffnen Sie die Website ohne Fastly und verwenden Sie die folgenden Schritte:'
exl-id: c0a4a9f8-a674-4cef-8088-e844594e6076
feature: Cache, Cloud
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%
---
# Adobe Commerce-Fehlerberichtnummer anstelle von Fastly 503-Fehler anzeigen

Standardmäßig werden in Fastly alle Adobe Commerce-Fehler hinter dem Fehler **503 Service Unavailable** ausgeblendet. Um die Nummer des Adobe Commerce-Fehlerprotokollberichts anzuzeigen (um sie in den Protokollen zu finden und die Fehlerdetails anzuzeigen), öffnen Sie die Website ohne Fastly und verwenden Sie die folgenden Schritte:

1. Fügen Sie die Domain und IP-Adresse Ihrer Anwendung zu Ihrer Hosts-Datei auf Ihrem lokalen Computer hinzu.
1. Löschen Sie den Browser-Cache und die Cookies (oder wechseln Sie in den Inkognito-Modus).
1. Öffnen Sie die Website Ihres Stores erneut, um den Adobe Commerce-Fehler anzuzeigen.

Sobald der Fehler „Authentische Adobe Commerce&quot; und die Fehlerberichtnummer angezeigt werden, können Sie Details in der Fehlerberichtsdatei erhalten, indem Sie die folgenden Schritte ausführen:

1. SSH in die betroffene Umgebung. Siehe [SSH für eine Umgebung](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) in unserer Entwicklerdokumentation.
1. Suchen Sie die `./var/report/{error_number}`.

## Hinzufügen der Anwendungsdomäne und der IP-Adresse zur Hosts-Datei: detaillierte Schritte

1. Überprüfen Sie die Server-IP Ihres Stores, indem Sie den `nslookup`-Befehl in der Befehlszeile auf Ihrem lokalen Computer ausführen:
   * Benutzer mit Pro-Architektur (Staging- und Produktionsumgebungen):

   ```
   nslookup {your_project_id}.ent.magento.cloud
   ```

   * Benutzer der Starter-Architektur (alle Umgebungen); Benutzer der Pro-Architektur (Integrationsumgebung):

   ```
   nslookup gw.{your_region}.magentosite.cloud
   ```

1. Fügen Sie Ihre Store-Domain und die Anwendungs-Server-IP im folgenden Format zur Hosts-Datei auf Ihrem lokalen Computer hinzu:

```
{server_IP} {store_domain}
```
