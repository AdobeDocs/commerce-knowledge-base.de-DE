---
title: Suchmaschine kann mit Commerce Admin nicht geändert werden (Menü "Suchmaschine"ist nicht verfügbar)
description: Dieser Artikel bietet eine Lösung zum Ändern der Adobe Commerce-Suchmaschine mithilfe des Commerce-Administrators, wenn das Feld Suchmaschine nicht angezeigt wird oder das Kontrollkästchen Systemwert verwenden ausgegraut ist und nicht zugänglich ist.
exl-id: 5b0f728c-6a8d-446d-9553-5abc3d01e516
feature: Admin Workspace, Search, Variables
role: Developer
source-git-commit: 0ea7bbef7fec556f9a90151be9cf1077f5cfac45
workflow-type: tm+mt
source-wordcount: '833'
ht-degree: 0%

---

# Suchmaschine kann mit Commerce Admin nicht geändert werden (Menü &quot;Suchmaschine&quot;ist nicht verfügbar)

>[!WARNING]
>
> [Die MySQL-Katalogsuchmaschine wird in Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md) entfernt. Sie müssen den Elasticsearch-Host vor der Installation von Version 2.4.0 eingerichtet und konfiguriert haben.
> 
> Siehe:
> [Installieren und konfigurieren Sie Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch).
> [Installieren und Konfigurieren von OpenSearch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/opensearch)
> [Live Search installieren und konfigurieren](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install)

Dieser Artikel bietet eine Lösung zum Ändern der Adobe Commerce-Suchmaschine mithilfe des Commerce-Administrators, wenn das Feld **Suchmaschine** nicht angezeigt wird oder das Kontrollkästchen **Systemwert verwenden** ausgegraut ist und nicht aufgerufen werden kann.

In diesem Artikel:

* [Betroffene Versionen](#affected-versions)
* [Suchmaschine mit Commerce Admin ändern (Schritte)](#change-search-engine-using-magento-admin-steps)
* [Probleme mit Adobe Commerce vor Ort](#magento-commerce-on-premise)
* [Adobe Commerce auf Cloud-Infrastruktur](#magento-commerce-cloud)

## Betroffene Versionen

* Adobe Commerce vor Ort: 2.4.X
* Adobe Commerce über Cloud-Infrastruktur:
   * Version: 2.4.X
   * Architektur des Einstiegs- und Pro-Plans
* MySQL, Elasticsearch, OpenSearch, Live Search: alle unterstützten Versionen

## Suchmaschine mit Admin ändern (Schritte)

1. Melden Sie sich bei **[!UICONTROL Admin]** als Administrator an.
1. Klicken Sie auf der linken Seite der **[!UICONTROL Admin]** -Seitenleiste auf **[!UICONTROL Stores]**.
1. Wählen Sie unter &quot;**[!UICONTROL Settings]**&quot;die Option &quot;**[!UICONTROL Configuration]**&quot;.
1. Navigieren Sie zum Bedienfeld auf der linken Seite unter **[!UICONTROL Catalog],** und wählen Sie **[!UICONTROL Catalog]**.
1. Erweitern Sie den Abschnitt **[!UICONTROL Catalog Search]** .    ![catalog_menu.png](assets/catalog_menu.png)
1. Gehen Sie zum Feld **[!UICONTROL Search Engine]** und entfernen Sie die Auswahl aus dem Kontrollkästchen **[!UICONTROL Use system value]** .
1. Klicken Sie auf das Menü **[!UICONTROL Search Engine]** und wählen Sie eine der folgenden verfügbaren Optionen aus:    ![search_engine_menu.png](assets/search_engine_menu.png)
1. Klicken Sie oben rechts auf der Seite auf **[!UICONTROL Save Config]** .

## Probleme mit Adobe Commerce vor Ort

### Problem 1: Das Suchmaschinenfeld wird nicht angezeigt

Wenn Sie auf den Abschnitt **Katalogsuche** zugreifen, wird das Menü **Suchmaschine** überhaupt nicht angezeigt.

![search_engine_not_displayed.png](assets/search_engine_not_displayed.png)

### Ursache: Die Store-Ansicht ist keine Standardkonfiguration

Für die Store-Ansicht für den Admin wurde ein anderer Wert als *Standardkonfiguration* festgelegt.

Bei der Suchmaschine handelt es sich um eine globale Konfiguration, die auf Anwendungsebene und nicht auf Store-Umfang festgelegt wird. Stores in einer Adobe Commerce-Anwendung können keine unterschiedlichen Suchmaschinen verwenden.

### Lösung: Legen Sie die Store-Ansicht auf Standardkonfiguration fest.

1. Melden Sie sich bei **[!UICONTROL Admin]** als Administrator an.
1. Klicken Sie auf der linken Seite der **[!UICONTROL Admin]** -Seitenleiste auf **[!UICONTROL Stores]**.
1. Navigieren Sie zu **[!UICONTROL Settings]** und wählen Sie **[!UICONTROL Configuration]** aus.
1. Klicken Sie in der oberen linken Ecke auf den Selektor **[!UICONTROL Store View]** und wählen Sie **[!UICONTROL *Standardkonfiguration *]**.
1. Klicken Sie im Bestätigungsdialogfeld auf &quot;**[!UICONTROL OK]**&quot;, um die Änderungen an der Store-Ansicht zu genehmigen.

![change_store_view.png](assets/change_store_view.png)

**Verwandte Dokumentation:** [Ändern des Umfangs](https://experienceleague.adobe.com/docs/commerce-admin/config/scope-change.html#set-the-scope) in unserem Benutzerhandbuch.

### Problem 2: &quot;Use system value&quot; kann nicht deaktiviert werden

Wenn Sie auf den Abschnitt **Katalogsuche** des Admin zugreifen, ist das Kontrollkästchen **Systemwert verwenden** grau ausgeblendet, sodass Sie die Auswahl nicht aus dem Kontrollkästchen entfernen können, um die Suchmaschine später zu ändern.

### Ursache

Die standardmäßige Suchmaschine wurde auf der Anwendungskonfigurationsebene in den Dateien `app/etc/env.php` oder `app/etc/config.php` konfiguriert und kann daher nicht mit dem Admin geändert werden.

Beispiel des Abschnitts mit standardmäßiger Suchmaschinenkonfiguration:

```php
'system'=>
array (
'default'=>
array (
'catalog'=>
array (
'search'=>
array (
'engine'=>'mysql',
),
),
),
),
```

### Lösung

Entfernen Sie den Abschnitt mit der standardmäßigen Suchmaschinenkonfiguration aus den Konfigurationsdateien `app/etc/env.php` oder `app/etc/config.php` .

### Verwandte Artikel in unserer Entwicklerdokumentation

[Adobe Commerce-Konfigurationsdateien](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/files/deployment-files.html) im Adobe Commerce-Konfigurationshandbuch

## Adobe Commerce auf Cloud-Infrastruktur

Der Wechsel von Suchmaschinen mithilfe von Admin ist in Adobe Commerce in der Cloud-Infrastruktur aufgrund der Organisation der Cloud-Infrastruktur nicht möglich.

Während des Bereitstellungsprozesses überprüfen die Adobe Commerce-Bereitstellungsskripte für Cloud-Infrastruktur, ob das Elasticsearch in der Variable `MAGENTO_CLOUD_RELATIONSHIPS` deklariert wurde. Wenn diese Option deklariert ist, wird Elasticsearch als aktive Suchmaschine ausgewählt und automatisch konfiguriert. Der Zugriff auf die [MySQL-Suchmaschine](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md) ist im Admin nicht mehr möglich. Wenn die Elasticsearch-Beziehung nicht deklariert wurde, ist MySQL auf &quot;aktiv&quot;gesetzt und der Zugriff auf Elasticsearch wird nicht mehr möglich.

Es wird nicht empfohlen, die Konfigurationsdateien `app/etc/env.php` oder `app/etc/config.php` direkt in Ihrer Cloud-Umgebung zu bearbeiten. Daher ist es nicht empfehlenswert, diese Dateien zu ändern, um die Elasticsearch-Engine zu erstellen, die in Admin angezeigt werden soll (die im vorherigen Abschnitt empfohlene Lösung).

### Suchmaschine in Staging- und Produktionsumgebungen ändern

Bevor Sie in Ihren Staging- und Produktionsumgebungen von MySQL zu Elasticsearch wechseln, stellen Sie sicher, dass Sie zuvor [ein Support-Ticket gesendet haben](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), um Elasticsearch in der Umgebung zu aktivieren, und das Ticket wurde erfolgreich behoben.

Um die in Ihren Staging- und Produktionsumgebungen verwendete Suchmaschine zu ändern, ändern Sie die Umgebungsvariable `SEARCH_CONFIGURATION` in Ihrer `.magento.env.yaml` -Datei in Ihrer lokalen Umgebung und fügen Sie dann Änderungen in die Integrations- und Staging-/Produktionsumgebungen ein, damit die Änderungen wirksam werden.

Wenn Sie zu Elasticsearch 7 wechseln, sieht die Variable &quot;SEARCH\_CONFIGURATION&quot;in der resultierenden `.magento.env.yaml`-Datei möglicherweise wie folgt aus:

```yaml
stage:
  deploy:
   SEARCH_CONFIGURATION:
     engine: elasticsearch7
     elasticsearch_server_hostname: hostname
     elasticsearch_server_port: '12345'
     elasticsearch_index_prefix: magento
     elasticsearch_server_timeout: '15'
```

Wenn Sie zu &quot;[OpenSearch&quot;(in 2.4.6 und höher)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/search-engine-shown-elasticsearch-despite-open-search)&quot;wechseln, könnte die Variable &quot;SEARCH\_CONFIGURATION&quot;in der resultierenden Datei &quot;`.magento.env.yaml`&quot;wie folgt aussehen:

```yaml
stage:
  deploy:
   SEARCH_CONFIGURATION:
     engine: opensearch
     elasticsearch_server_hostname: hostname
     elasticsearch_server_port: '12345'
     elasticsearch_index_prefix: magento
     elasticsearch_server_timeout: '15'
```

Wenn Sie [ zur Live-Suche wechseln](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/error-opensearch-search-engine-doesnt-exist-falling-back-to-livesearch), sieht die Variable &quot;SEARCH\_CONFIGURATION&quot;in der resultierenden `.magento.env.yaml`-Datei möglicherweise wie folgt aus:

```yaml
stage:
  deploy:
   SEARCH_CONFIGURATION:
     engine: livesearch
```

### Verwandte Dokumentation

#### Support-Wissensdatenbank

* [Elasticsearch in Cloud aktivieren](/help/how-to/general/enable-elasticsearch-on-cloud.md)

#### Entwicklerdokumentation

* [Einrichten des Elasticsearch-Dienstes](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch.html)
* [Erstellen und Bereitstellen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) (Dokumentation zur Konfigurationsdatei `.magento.env.yaml`)
* [Variablen bereitstellen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html) ([SEARCH\_CONFIGURATION section](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#search_configuration))
* [Dienste](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) (Dokumentation zur Konfigurationsdatei `.magento/services.yaml`)
* [Live Search](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/overview)
