---
title: Das oberste Navigationsfenster wird nicht auf der Storefront geladen
description: Dieser Artikel bietet Konfigurationslösungen für die verschiedenen ESI-Probleme (Varnish Edge Side Includes), bei denen der Inhalt bestimmter Seiten, normalerweise das obere Navigationsfenster, nicht auf der Storefront angezeigt wird, wenn Varnish für das Caching verwendet wird.
exl-id: e7f9b773-1a2d-4c3b-9e1f-a1781fbc898c
feature: Categories, Site Navigation, Storefront, Variables
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Das oberste Navigationsfenster wird nicht auf der Storefront geladen

Dieser Artikel bietet Konfigurationslösungen für die verschiedenen ESI-Probleme (Varnish Edge Side Includes), bei denen der Inhalt bestimmter Seiten, normalerweise das obere Navigationsfenster, nicht auf der Storefront angezeigt wird, wenn Varnish für das Caching verwendet wird.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.X.X
* Alle verschiedenen Versionen

## Problem

<u>Voraussetzungen</u>:

Installieren und konfigurieren Sie Varnish für Ihren Adobe Commerce-Store.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zur Storefront.
1. Durchsuchen Sie die Store-Seiten.

<u>Erwartete Ergebnisse</u>:

Alle Inhalte und alle Seitenblöcke werden erfolgreich geladen.

<u>Tatsächliche Ergebnisse</u>:

Beachten Sie, dass einige Inhaltsbausteine, wie das obere Navigationsfenster mit Kategorien, nicht geladen werden. Stattdessen wird ein leeres Leerzeichen angezeigt.

## Ursache

Mögliche Gründe für das Problem sind die folgenden:

* ESI-Include-Tags werden mit dem HTTPS-Zugriffsprotokoll generiert, während Varnish nur mit HTTP funktioniert.
* In JSON wird ESI nicht in Spanisch verarbeitet.
* Antwortheader sind zu groß für Varnish; sie können nicht verarbeitet werden.

## Lösung

Um die Probleme zu beheben, müssen Sie eine zusätzliche Varnish-Konfiguration durchführen und Varnish neu starten.

1. Als Benutzer mit `root` -Berechtigungen öffnen Sie die Konfigurationsdatei &quot;Vanish&quot;in einem Texteditor. Weitere Informationen dazu, wo sich diese Datei für verschiedene Betriebssysteme befindet, finden Sie in der Entwicklerdokumentation unter [Ändern der Konfiguration des Varnish-Systems](https://devdocs.magento.com/guides/v2.3/config-guide/varnish/config-varnish-configure.html#config-varnish-config-sysvcl) .
1. Fügen Sie im `DAEMON_OPTS variable` `-p feature=+esi_ignore_https`, `-p  feature=+esi_ignore_other_elements`, `-p  feature=+esi_disable_xml_check` hinzu. Dies würde wie folgt aussehen:

   ```bash
   DAEMON_OPTS="-a :6081 \    -p feature=+esi_ignore_other_elements \    -p feature=+esi_disable_xml_check \    -p feature=+esi_ignore_https \    -T localhost:6082 \    -f /etc/varnish/default.vcl \    -S /etc/varnish/secret \    -s malloc,256m"
   ```

1. Speichern Sie Ihre Änderungen und beenden Sie den Texteditor.
1. Erhöhen Sie in der VCL-Konfigurationsdatei die Antwortheader, indem Sie die Werte dieser Parameter erhöhen: `http_resp_hdr_len`, `http_resp_size`, `workspace_backend`. Stellen Sie sicher, dass die letzten beiden Werte ähnliche Werte aufweisen.
1. Wenn Sie dies ändern, müssen Sie `service varnish restart` ausführen, damit die Änderungen wirksam werden.

## Verwandtes Lesen

* [Konfigurieren Sie Varnish und Ihren Webserver](https://devdocs.magento.com/guides/v2.3/config-guide/varnish/config-varnish-configure.html#config-varnish-config-sysvcl) in unserer Entwicklerdokumentation.
* [Varnish-Dokumentation](https://varnish-cache.org/docs/5.1/reference/index.html)
