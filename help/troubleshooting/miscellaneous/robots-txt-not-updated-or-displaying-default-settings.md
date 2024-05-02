---
title: robots.txt wird nicht aktualisiert oder zeigt Standardeinstellungen an
description: Der Artikel bietet eine Lösung für Fälle, in denen Sie "robots.txt"richtig konfiguriert haben, z. B. per [Best Practices für Adobe Commerce robots.txt](https://support.magento.com/hc/en-us/articles/360048754931), aber die Datei "robots.txt"wird nicht aktualisiert oder zeigt die Standardeinstellungen an.
exl-id: 629b1247-9282-49f9-ada3-a804ddbaa0f5
feature: Configuration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# robots.txt wird nicht aktualisiert oder zeigt Standardeinstellungen an

Der Artikel bietet eine Lösung für den Fall, dass Sie `robots.txt` korrekt, z. B. pro [Best Practices für Adobe Commerce robots.txt](https://support.magento.com/hc/en-us/articles/360048754931) aber die `robots.txt` wird nicht aktualisiert oder zeigt die Standardeinstellungen an.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.3.x, 2.4.x

## Problem

Die Standardeinstellung kann nicht geändert werden `robots.txt` -Einstellung.

<u>Zu reproduzierende Schritte:</u>

1. Rufen Sie das Admin-Bedienfeld auf.
1. Hinzufügen von Inhalten zu **Inhalt** > Design > **Konfiguration** > **Benutzerdefinierte Anweisung bearbeiten von`robots.txt`** -Datei, z. B. den Text &quot;hello&quot;und speichern Sie die Änderungen.
1. Besuchen Sie die `robots.txt` url.

<u>Erwartetes Ergebnis:</u>
`robots.txt` hat den gespeicherten Text.

<u>Ergebnis:</u>

`robots.txt` -Datei nicht geändert.

## Ursache

Die Indizierung durch Suchmaschinen ist deaktiviert.

## Lösung

Aktivieren Sie die Indizierung durch Suchmaschinen. Siehe [Konfigurieren der Indizierung nach Suchmaschine](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html#configure-indexing-by-search-engine) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

* [Sitemap- und Suchmaschinenroboter hinzufügen](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) in unserer Entwicklerdokumentation.
