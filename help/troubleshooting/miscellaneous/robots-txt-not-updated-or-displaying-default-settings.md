---
title: robots.txt wird nicht aktualisiert oder zeigt Standardeinstellungen an
description: Der Artikel bietet eine Lösung für Fälle, in denen Sie "robots.txt"richtig konfiguriert haben, z. B. per [Best Practices für Adobe Commerce robots.txt](https://support.magento.com/hc/en-us/articles/360048754931), aber die Datei "robots.txt"wird nicht aktualisiert oder zeigt die Standardeinstellungen an.
exl-id: 629b1247-9282-49f9-ada3-a804ddbaa0f5
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# robots.txt wird nicht aktualisiert oder zeigt Standardeinstellungen an

Der Artikel bietet eine Lösung für Fälle, in denen Sie `robots.txt` richtig konfiguriert haben, z. B. gemäß den Best Practices für Adobe Commerce robots.txt](https://support.magento.com/hc/en-us/articles/360048754931) , die `robots.txt` jedoch nicht aktualisiert wird oder die Standardeinstellungen anzeigt.[

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.3.x, 2.4.x

## Problem

Die Standardeinstellung `robots.txt` kann nicht geändert werden.

<u>Zu reproduzierende Schritte:</u>

1. Rufen Sie das Admin-Bedienfeld auf.
1. Fügen Sie Inhalt zu **Inhalt** > Design > **Konfiguration** > **Benutzerdefinierte Anweisung der Datei`robots.txt`** hinzu, z. B. den Text &quot;hello&quot;und speichern Sie die Änderungen.
1. Besuchen Sie die URL `robots.txt` .

<u>Erwartetes Ergebnis:</u>
`robots.txt` hat den gespeicherten Text.

<u>Tatsächliches Ergebnis:</u>

Die Datei &quot;`robots.txt`&quot; ändert sich nicht.

## Ursache

Die Indizierung durch Suchmaschinen ist deaktiviert.

## Lösung

Aktivieren Sie die Indizierung durch Suchmaschinen. Siehe [Konfigurieren der Indizierung durch Suchmaschine](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap#configure-indexing-by-search-engine) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

* [Fügen Sie in unserer Entwicklerdokumentation Sitemap und Suchmaschinen-Roboter hinzu](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap).
