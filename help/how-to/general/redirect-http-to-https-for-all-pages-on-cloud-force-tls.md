---
title: Umleiten von HTTP zu HTTPS für alle Seiten in Adobe Commerce in der Cloud-Infrastruktur (TLS erzwingen)
description: Aktivieren Sie die Funktion "TLS erzwingen"von Fastly in Commerce Admin, um die globale HTTP-zu-HTTPS-Umleitung für alle Seiten Ihrer Adobe Commerce im Cloud-Infrastrukturspeicher zu aktivieren.
exl-id: 71667f52-a99a-47a6-99d8-10532364870f
feature: Cache, Cloud
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# Umleiten von HTTP zu HTTPS für alle Seiten in Adobe Commerce in der Cloud-Infrastruktur (TLS erzwingen)

Aktivieren Sie die Funktion &quot;**TLS erzwingen**&quot;von Fastly in Commerce Admin, um die globale HTTP- zu HTTPS-Umleitung für alle Seiten Ihrer Adobe Commerce im Cloud-Infrastrukturspeicher zu aktivieren.

Dieser Artikel enthält detaillierte [Schritte](#steps), einen kurzen Überblick über die Funktion &quot;TLS erzwingen&quot;, die betroffenen Versionen und Links zur zugehörigen Dokumentation.

## Schritte {#steps}

### Schritt 1: Sichere URLs konfigurieren {#step-1-configure-secure-urls}

In diesem Schritt definieren wir die sicheren URLs für den Store. Wenn dies bereits geschehen ist, gehen Sie zu [Schritt 2: TLS erzwingen aktivieren](#step-2-enable-force-tls).

1. Melden Sie sich bei Commerce Admin an.
1. Navigieren Sie zu **Stores** > **Konfiguration** > **Allgemein** > **Web**.
1. Erweitern Sie den Abschnitt **Basis-URLs (sicher)** .    ![magento-admin_base-urls-secure.png](assets/magento-admin_base-urls-secure.png)
1. Geben Sie im Feld **Sichere Basis-URL** die HTTPS-URL Ihres Stores an.
1. Stellen Sie die Einstellungen **Sichere URLs in Storefront verwenden** und **Sichere URLs in Admin** verwenden auf **Ja** ein.    ![magento-admin_base-urls-secure-settings.png](assets/magento-admin_base-urls-secure-settings.png)
1. Klicken Sie oben rechts auf **Konfiguration speichern** , um Änderungen anzuwenden.

**Verwandte Dokumentation in unserem Benutzerhandbuch:**   [URLs speichern](https://docs.magento.com/m2/ee/user_guide/stores/store-urls.html).

### Schritt 2: TLS erzwingen aktivieren {#step-2-enable-force-tls}

1. Navigieren Sie im Commerce-Admin zu &quot;**Stores**&quot;> &quot;**Konfiguration**&quot;> &quot;**Erweitert**&quot;> &quot;**System**&quot;.
1. Erweitern Sie den Abschnitt **Vollständiger Seiten-Cache** , dann den Abschnitt **Schnelle Konfiguration** und dann den Abschnitt **Erweiterte Konfiguration**.
1. Klicken Sie auf die Schaltfläche **TLS erzwingen** .    ![magento-admin_force-tls-button.png](assets/magento-admin_force-tls-button.png)
1. Klicken Sie im angezeigten Dialogfeld auf **Upload**.    ![magento-admin_force-tls-validation-dialog.png](assets/magento-admin_force-tls-confirmation-dialog.png)
1. Stellen Sie nach dem Schließen des Dialogfelds sicher, dass der aktuelle Status von Force TLS als **enabled** angezeigt wird.    ![magento-admin_force-tls-enabled.png](assets/magento-admin_force-tls-enabled.png)

**Verwandte schnelle Dokumentation:**   [TLS-Handbuch erzwingen](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/FORCE-TLS.md) für Adobe Commerce 2.

## Über TLS erzwingen

TLS (Transport Layer Security) ist ein Protokoll für sichere HTTP-Verbindungen, das seinen weniger sicheren Vorgänger ersetzt - das SSL-Protokoll (Secure Socket Layer).

Mit der Funktion TLS erzwingen von Fastly können Sie alle eingehenden unverschlüsselten Anfragen für Ihre Siteseiten zu TLS zwingen.

>>
Es funktioniert durch die Rückgabe einer Antwort vom Typ *301 Dauerhaft verschoben* auf eine unverschlüsselte Anforderung, die zur TLS-Entsprechung umleitet. Wenn Sie beispielsweise eine Anforderung für *http://www.example.com/foo.jpeg* stellen, werden Sie zu *https://www.example.com/foo.jpeg* umgeleitet.

[Sicherheit der Kommunikation](https://docs.fastly.com/guides/securing-communications/) (schnelle Dokumentation)

## Betroffene Versionen

* **Adobe Commerce in der Cloud-Infrastruktur:**
   * Version: 2.1.4 und höher
   * Pläne: Adobe Commerce zur Starter-Planarchitektur der Cloud-Infrastruktur und Adobe Commerce zur Cloud Infrastructure Pro-Planarchitektur (einschließlich Pro Legacy)
* **Fastly:** 1.2.4

## Keine Änderungen erforderlich in routes.yaml

Um die HTTP- zu HTTPS-Umleitung auf **allen** Seiten Ihres Stores zu aktivieren, müssen Sie die Seiten nicht zur Konfigurationsdatei `routes.yaml` hinzufügen. Die globale Aktivierung von TLS erzwingen für Ihren gesamten Speicher (unter Verwendung des Commerce-Administrators) reicht aus.

## Verwandte Schnelldokumentation

* [TLS-Handbuch für Adobe Commerce erzwingen 2](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/FORCE-TLS.md)
* [Erzwingen einer TLS-Umleitung](https://docs.fastly.com/guides/securing-communications/forcing-a-tls-redirect)
* [ Sicherheit der Kommunikation](https://docs.fastly.com/guides/securing-communications/)
