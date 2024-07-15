---
title: Hauptmenü (Kategorien) wird nicht auf Unterseiten mit Fastly-Aktivierung angezeigt
description: Dieser Artikel enthält eine Fehlerbehebung für den Fall, dass das Hauptmenü (oder das [Menü "Top-Navigation"](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) in unserem Benutzerhandbuch) nicht auf der Storefront für Unterseiten angezeigt wird (z. B. *blog/page*), wenn Fastly oder Varnish aktiviert ist.
exl-id: 7c54791d-8aa6-4f01-a28b-a7aecdb8ff74
feature: Categories, Marketing Tools
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Hauptmenü (Kategorien) wird nicht auf Unterseiten mit Fastly-Aktivierung angezeigt

Dieser Artikel enthält eine Fehlerbehebung für den Fall, dass das Hauptmenü (oder das oberste Navigationsmenü der Kategorie [in unserem Benutzerhandbuch) nicht auf der Storefront für Unterseiten angezeigt wird (z. B. *Blog/Seite*), wenn Fastly oder Varnish aktiviert ist.](/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html)

**Ursache:** das nicht zulässige `/` Zeichen (Schrägstrich) im Parameter *URL-Schlüssel* der Seite (Suchmaschinenoptimierungseinstellungen). Das Zeichen wird normalerweise hinzugefügt, wenn *URL-Pfad* (mit dem gesamten Seitenspeicherort) fälschlicherweise anstelle von *URL-Schlüssel* angegeben wird: Beispiel: *blog/page\_name* anstelle von nur *page\_name*.

**Lösung:** Entfernen Sie das Zeichen `/` (Schrägstrich). Geben Sie für den Parameter *URL-Schlüssel* nur den Seitennamen an.

## Betroffene Versionen

* Adobe Commerce On-Premise 2.X.X
* Adobe Commerce auf Cloud-Infrastruktur 2.X.X
* Fastal oder Varnisch

## Problem

Das Hauptmenü (in unserem Benutzerhandbuch auch als [Kategorieoberer Navigationsmenü](/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) bezeichnet) wird nicht auf der Storefront für Unterseiten angezeigt, wenn Fastly oder andere auf Varnish basierende Dienste aktiviert sind.

## Ursache

Das Problem wird durch das nicht zulässige `/` -Zeichen (Schrägstrich) verursacht, das zum Parameter *URL-Schlüssel* hinzugefügt wurde (Suchmaschinenoptimierungseinstellungen).

Das Zeichen wird normalerweise hinzugefügt, wenn *URL-Pfad* (mit dem gesamten Seitenspeicherort, einschließlich der übergeordneten Ressource/des Ordners der Seite) fälschlicherweise anstelle von *URL-Schlüssel* angegeben wird: Beispiel: *blog/page\_name* anstelle von nur *page\_name*.

![URL-Schlüsselparameter für SEO-Einstellungen](assets/seo_url_key.png)

## Lösung

Entfernen Sie das Zeichen `/` (Schrägstrich) aus dem Parameter *URL-Schlüssel* für alle Seiten Ihres Stores.

Verwenden Sie also *URL-Schlüssel* anstelle von *URL-Pfad*: Erwähnen Sie nur den Seitennamen ohne übergeordnete Ressource/Verzeichnis.

### Recommendations in Seitenhierarchie und SEO

Verwenden Sie zum Festlegen der Seitenhierarchie den Abschnitt **Hierarchie** im Menü &quot;Seite bearbeiten&quot;.

![Hierarchieeinstellungen](assets/hierarchy_hr.png)

Für komplexere Hierarchielösungen können Sie auch das Menü **Inhalt** > **Elemente** > **Hierarchie** verwenden.

Verwenden Sie für SEO-Zwecke auf Produktseiten URL-Neuschreibungen (**Marketing** > **SEO und Suche** > **URL-Neuschreibungen**).

## Weitere Informationen finden Sie in unserem Benutzerhandbuch

Der Parameter *URL-Schlüssel* für SEO:

* [Suchmaschinenoptimierung](/docs/commerce-admin/catalog/categories/create/categories-search-engine-optimization.html)
* [Hinzufügen einer neuen Seite](/docs/commerce-admin/content-design/elements/pages/page-add.html)

Seitenhierarchie:

* [Übersicht](/docs/commerce-admin/content-design/elements/pages/page-hierarchy.html)
* [Knoten hinzufügen](/docs/commerce-admin/content-design/elements/pages/page-hierarchy.html#add-a-hierarchy-node)
