---
title: Hauptmenü (Kategorien) wird nicht auf Unterseiten angezeigt, wenn Fastly aktiviert ist
description: Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass das Hauptmenü (oder das [Menü für die obere Navigation der Kategorie](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) in unserem Benutzerhandbuch) nicht auf der Storefront für Unterseiten angezeigt wird (z. B. *blog/page*), wenn Fastly oder Varnish aktiviert ist.
exl-id: 7c54791d-8aa6-4f01-a28b-a7aecdb8ff74
feature: Categories, Marketing Tools
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Hauptmenü (Kategorien) wird nicht auf Unterseiten angezeigt, wenn Fastly aktiviert ist

Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass das Hauptmenü (oder das [Menü „Navigation oben“ ](/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) unserem Benutzerhandbuch) nicht auf der Storefront für Unterseiten angezeigt wird (z. B. *blog/page*), wenn Fastly oder Varnish aktiviert ist.

**Ursache:** das nicht zulässige `/` (Schrägstrich) im Parameter *URL-Schlüssel* der Seite (Einstellungen für die Suchmaschinenoptimierung). Das Zeichen wird normalerweise hinzugefügt, wenn *URL-Pfad* (mit dem gesamten Seitenspeicherort) versehentlich anstelle des *URL-Schlüssels* angegeben wird, z. B. *blog/page\_name* anstelle von *page\_name*.

**Lösung:** entfernen Sie das `/` Zeichen (Schrägstrich). Geben Sie für den Parameter *URL-Schlüssel* nur den Seitennamen an.

## Betroffene Versionen

* Adobe Commerce On-Premises 2.X.X
* Adobe Commerce auf Cloud-Infrastruktur 2.x.x
* Fastly oder Lack

## Problem

Das Hauptmenü (in unserem Benutzerhandbuch auch als [Kategorie-Navigationsmenü oben](/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) bezeichnet) wird auf der Storefront für Unterseiten nicht angezeigt, wenn Fastly oder andere lackbasierte Dienste aktiviert sind.

## Ursache

Das Problem wird durch das nicht zulässige `/` (Schrägstrich) verursacht, das zum Parameter *URL-Schlüssel* hinzugefügt wurde (Einstellungen für die Suchmaschinenoptimierung).

Das Zeichen wird normalerweise hinzugefügt, wenn *URL-Pfad* (mit dem gesamten Seitenspeicherort, einschließlich der übergeordneten Ressource/des übergeordneten Verzeichnisses der Seite) versehentlich anstelle von *URL-Schlüssel* angegeben wird, z. B. *blog/page\_name* anstelle von nur *page\_name*.

![URL-Schlüsselparameter für SEO-Einstellungen](assets/seo_url_key.png)

## Lösung

Entfernen Sie das `/` (Schrägstrich) aus dem *URL Key*-Parameter für alle Seiten Ihres Stores.

Mit anderen Worten: Verwenden Sie *URL-Schlüssel* anstelle von *URL-Pfad*: geben Sie nur den Seitennamen an, ohne die übergeordnete Ressource/das übergeordnete Verzeichnis.

### Recommendations in Seitenhierarchie und SEO

Um die Seitenhierarchie festzulegen, verwenden Sie den **Hierarchie** des Menüs Seite bearbeiten .

![Hierarchieeinstellungen](assets/hierarchy_hr.png)

Sie können auch das Menü **Inhalt** > **Elemente** > **Hierarchie** für komplexere Hierarchielösungen verwenden.

Verwenden Sie für SEO-Zwecke auf Produktseiten URL-Neuschreibungen (**Marketing** > **SEO und Suche** > **URL-Neuschreibungen**).

## Weitere Informationen in unserem Benutzerhandbuch

Der *URL-Schlüssel* für SEO:

* [Suchmaschinenoptimierung](/docs/commerce-admin/catalog/categories/create/categories-search-engine-optimization.html)
* [Hinzufügen einer neuen Seite](/docs/commerce-admin/content-design/elements/pages/page-add.html)

Seitenhierarchie:

* [Übersicht](/docs/commerce-admin/content-design/elements/pages/page-hierarchy.html)
* [Hinzufügen eines Knotens](/docs/commerce-admin/content-design/elements/pages/page-hierarchy.html#add-a-hierarchy-node)
