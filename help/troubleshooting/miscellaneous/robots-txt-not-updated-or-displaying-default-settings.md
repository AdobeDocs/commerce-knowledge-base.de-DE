---
title: robots.txt nicht aktualisiert oder zeigt Standardeinstellungen an
description: Der Artikel bietet eine Lösung für den Fall, dass Sie „robots.txt“ korrekt konfiguriert haben, z. B. gemäß [Best Practices für Adobe Commerce robots.txt](https://support.magento.com/hc/en-us/articles/360048754931), aber „robots.txt“ nicht aktualisiert wird oder die Standardeinstellungen anzeigt.
exl-id: 629b1247-9282-49f9-ada3-a804ddbaa0f5
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# robots.txt nicht aktualisiert oder zeigt Standardeinstellungen an

Der Artikel bietet eine Lösung für den Fall, dass Sie `robots.txt` richtig konfiguriert haben, z. B. [Best Practices für Adobe Commerce robots.txt](https://support.magento.com/hc/en-us/articles/360048754931), die `robots.txt` jedoch nicht aktualisiert wird oder die Standardeinstellungen anzeigt.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.3.x, 2.4.x

## Problem

Die `robots.txt` kann nicht geändert werden.

<u>Schritte zur Reproduktion:</u>

1. Rufen Sie das Admin-Bedienfeld auf.
1. Fügen Sie Inhalte zu **Inhalt** > Design > **Konfiguration** > **Bearbeiten Sie benutzerdefinierte Anweisungen`robots.txt`** Datei, z. B. den Text „Hallo“ und speichern Sie die Änderungen.
1. Rufen Sie die `robots.txt` URL auf.

<u>Erwartetes Ergebnis:</u>
`robots.txt` hat den gespeicherten Text.

<u>Tatsächliches Ergebnis:</u>

`robots.txt` Datei ändert sich nicht.

## Ursache

Die Indizierung durch Suchmaschinen ist deaktiviert.

## Lösung

Aktivieren der Indizierung durch Suchmaschinen. Siehe [Konfigurieren der Indizierung nach ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap#configure-indexing-by-search-engine)) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

* [Hinzufügen von Sitemap- und Suchmaschinenrobotern](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap) in unserer Entwicklerdokumentation.
