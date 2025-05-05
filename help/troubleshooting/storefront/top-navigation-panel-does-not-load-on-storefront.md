---
title: Oberes Navigationsfenster wird nicht in Storefront geladen
description: In diesem Artikel finden Sie Konfigurationslösungen für ESI-Probleme (Varnish Edge Side Includes), bei denen der Inhalt bestimmter Seiten, normalerweise das obere Navigationsfenster, nicht auf der Storefront angezeigt wird, wenn Varnish zum Caching verwendet wird.
exl-id: e7f9b773-1a2d-4c3b-9e1f-a1781fbc898c
feature: Categories, Site Navigation, Storefront, Variables
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Oberes Navigationsfenster wird nicht in Storefront geladen

In diesem Artikel finden Sie Konfigurationslösungen für ESI-Probleme (Varnish Edge Side Includes), bei denen der Inhalt bestimmter Seiten, normalerweise das obere Navigationsfenster, nicht auf der Storefront angezeigt wird, wenn Varnish zum Caching verwendet wird.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.x.x
* Alle Lackversionen

## Problem

<u>Voraussetzungen</u>:

Installieren und konfigurieren Sie Varnish für Ihren Adobe Commerce-Store.

<u>Schritte zur Reproduktion</u>:

1. Geh zum Laden.
1. Durchsuchen Sie die Store-Seiten.

<u>Erwartete Ergebnisse</u>:

Alle Inhalte und Seitenblöcke wurden erfolgreich geladen.

<u>Tatsächliche Ergebnisse</u>:

Beachten Sie, dass einige Inhaltsblöcke, z. B. das obere Navigationsfenster mit Kategorien, nicht geladen werden. Stattdessen wird Leerraum angezeigt.

## Ursache

Mögliche Gründe für das Problem sind:

* ESI Include-Tags werden mit dem HTTPS-Zugriffsprotokoll generiert, während Varnish nur mit HTTP funktioniert.
* Lack verarbeitet ESI nicht innerhalb von JSON.
* Antwort-Header sind zu groß für „Lackieren“; sie können nicht verarbeitet werden.

## Lösung

Um die Probleme zu beheben, müssen Sie eine zusätzliche Lackkonfiguration durchführen und Varnish neu starten.

1. Wenn Sie ein Benutzer mit `root` Berechtigungen sind, öffnen Sie Ihre Vanish-Konfigurationsdatei in einem Texteditor. Unter [Ändern der Konfiguration des Lacksystems](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/cache/config-varnish-server) in unserer Entwicklerdokumentation finden Sie Informationen darüber, wo sich diese Datei für verschiedene Betriebssysteme befinden könnte.
1. Fügen Sie in der `DAEMON_OPTS variable` `-p feature=+esi_ignore_https`, `-p  feature=+esi_ignore_other_elements`, `-p  feature=+esi_disable_xml_check` hinzu. Dies würde wie folgt aussehen:

   ```bash
   DAEMON_OPTS="-a :6081 \    -p feature=+esi_ignore_other_elements \    -p feature=+esi_disable_xml_check \    -p feature=+esi_ignore_https \    -T localhost:6082 \    -f /etc/varnish/default.vcl \    -S /etc/varnish/secret \    -s malloc,256m"
   ```

1. Speichern Sie Ihre Änderungen und beenden Sie den Texteditor.
1. Erhöhen Sie in der VCL-Konfigurationsdatei die Antwort-Header, indem Sie die Werte dieser Parameter erhöhen: `http_resp_hdr_len`, `http_resp_size`, `workspace_backend`. Stellen Sie sicher, dass die letzten beiden ähnliche Werte haben.
1. Wenn Sie dies ändern, müssen Sie `service varnish restart` ausführen, damit die Änderungen wirksam werden.

## Verwandtes Lesen

* [Konfigurieren Sie Lack und Ihren Webserver](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/cache/config-varnish-server) in unserer Entwicklerdokumentation.
* [Lackdokumentation](https://varnish-cache.org/docs/5.1/reference/index.html)
