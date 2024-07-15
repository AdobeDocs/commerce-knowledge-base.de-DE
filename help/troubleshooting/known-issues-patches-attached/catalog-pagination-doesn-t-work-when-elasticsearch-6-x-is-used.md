---
title: Katalogpaginierung funktioniert nicht mit Elasticsearch 6.x
description: Dieser Artikel enthält einen Patch für das Adobe Commerce-Problem, bei dem die Katalogpaginierung auf Elasticsearch 6.x nicht funktioniert.
exl-id: 60a423de-cf3a-4d73-a7cf-b6d9e95042ca
feature: Catalog Management, Categories, Search, Services
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Katalogpaginierung funktioniert nicht mit Elasticsearch 6.x

Dieser Artikel enthält einen Patch für das Adobe Commerce-Problem, bei dem die Katalogpaginierung auf Elasticsearch 6.x nicht funktioniert.

Mit dem folgenden Patch werden Probleme behoben, die bei Bereitstellungen, in denen Elasticsearch 6.x als Katalogsuchmaschine verwendet wird, bei Benutzern der Adobe Commerce 2.3.3-Erfahrung aufgetreten sind. Benutzern wird eine Fehlermeldung angezeigt, wenn sie versuchen, über die erste Seite der Suchergebnisse zu navigieren.

Nachdem dieser Patch installiert wurde, können Benutzer alle Suchergebnisse durchblättern.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.3.3
* Adobe Commerce vor Ort 2.3.3
* Magento Open Source 2.3.3
* Elasticsearch 6.x

## Problem

Es wurde ein Problem in Magento Open Source, Adobe Commerce On-Premise und Adobe Commerce in der Cloud-Infrastruktur entdeckt, bei dem die Seitenumschaltung bei einem Seitenwechsel nicht funktioniert.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie Adobe Commerce.
1. Aktivieren Sie Elasticseach 6 als Katalogsuchmaschine.
1. Fügen Sie der Kategorie eine Reihe von Produkten hinzu, die über das in Admin festgelegte 1-Seiten-Limit hinausgehen. **Hinweis**: 12 ist die Standardanzahl der Produkte, die pro Seite in Adobe Commerce 2.3.3 angezeigt werden.
1. Öffnen Sie Kategorie auf Storefront (entweder Suchergebnisse oder Kategorieseite) und gehen Sie zu Seite 2.

<u>Erwartetes Ergebnis</u>:

Produkte sollten auf der zweiten Seite angezeigt werden.

<u>Tatsächliches Ergebnis</u>:

**&quot;***Wir können keine Produkte finden, die mit der Nachricht &quot;selection***&quot;** übereinstimmen, die auf der zweiten Seite angezeigt wird.

## Lösung

Um das Problem zu beheben, wenden Sie bitte den an diesen Artikel angehängten Patch an. Scrollen Sie zum Herunterladen nach unten zum Ende des Artikels und klicken Sie auf den Dateinamen oder auf den folgenden Link:

[Problem mit der Katalogpaginierung beim Patch 6.x herunterladen](assets/Catalog_pagination_issue_on_Elasticsearch_6_composer-2019-10-11-08-07-41.patch.zip) - Der Patch ist mit allen betroffenen Versionen und Editionen kompatibel.

>[!WARNING]
>
>Adobe empfiehlt dringend, das Pflaster so schnell wie möglich anzuwenden, auch wenn Sie keine Symptome hatten.

## Anwenden des Pflasters

Anweisungen finden Sie unter [Anwenden eines von Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) bereitgestellten Composer-Patches.

## Attached files
