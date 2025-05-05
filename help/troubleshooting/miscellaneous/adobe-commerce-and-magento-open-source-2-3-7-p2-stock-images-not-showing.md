---
title: Stock-Bilder nicht angezeigt, Adobe Commerce und Magento Open Source 2.3.7-p2
description: Dieser Artikel bietet eine Lösung für das Problem, dass Adobe-Stock-Bilder, die in die Dateisystemverzeichnisse „pub/media“ oder „pub/media/catalog“ hochgeladen wurden, nicht in der Media Gallery-Benutzeroberfläche angezeigt werden. Dies liegt daran, dass sich die Bilder außerhalb der zulässigen Mediensammlungsverzeichnisse befinden. Damit diese Bilder angezeigt werden können, müssen Händler die Bilder im Dateisystem löschen und erneut in ein zugelassenes Mediensammlungsverzeichnis hochladen.
exl-id: 84488d87-095f-4739-858f-19a52d6e5822
feature: Categories, Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# Stock-Bilder nicht angezeigt, Adobe Commerce und Magento Open Source 2.3.7-p2

Dieser Artikel bietet eine Lösung für das Problem, dass Adobe-Stock-Bilder, die in Dateisystemverzeichnisse hochgeladen wurden, `pub/media` oder `pub/media/catalog` nicht in der Media Gallery-Benutzeroberfläche angezeigt werden. Dies liegt daran, dass sich die Bilder außerhalb der zulässigen Mediensammlungsverzeichnisse befinden. Damit diese Bilder angezeigt werden können, müssen Händler die Bilder im Dateisystem löschen und erneut in ein zugelassenes Mediensammlungsverzeichnis hochladen.

## Betroffene Produkte und Versionen

* Adobe Commerce und Magento Open Source 2.3.7-p2


## Problem

Händler können Adobe Stock-Bilder in den Speicherstamm der Mediensammlung hochladen, diese Bilder werden jedoch nicht in der Benutzeroberfläche angezeigt und erscheinen so, als wären sie nicht hochgeladen worden. Dies liegt daran, dass das System bemerkt, dass das Bild bereits in das Dateisystem hochgeladen wurde, obwohl es nicht in der Media Gallery-Benutzeroberfläche verfügbar ist. Das bedeutet, dass Händler, sobald sie ein Bild in `pub/media` oder `pub/media/catalog` hochladen, dieses Bild erst verwenden können, wenn es direkt im Dateisystem gelöscht wird.

<u>Schritte zur Reproduktion</u>

1. Aktivieren von Adobe Stock mit gültigen API-Schlüsseln.
1. Öffnen Sie die Mediensammlung (**Katalog** > **Kategorien** > **Inhalt** Abschnitt > klicken Sie **Aus Galerie auswählen**).
1. Klicken Sie **Adobe Stock durchsuchen**.
1. Bild auswählen. Klicken Sie auf **Vorschau speichern**. Beachten Sie, dass Sie das Adobe Stock-Raster möglicherweise zurücksetzen müssen, damit Bilder angezeigt werden.

<u>Erwartetes Ergebnis</u>:

Das Bild wird angezeigt.

<u>Tatsächliches </u>:

Eine Fehlermeldung wird angezeigt: *Das Bild kann nicht gefunden werden. Wir können dieses Bild nicht in der Mediensammlung finden.*

## Ursache

Bilder können über Adobe Stock in den Media Gallery-Speicherstamm hochgeladen werden.

## Lösung

Wählen Sie ein beliebiges Unterverzeichnis des Mediensammlungs-Stammverzeichnisses aus (außer **Stammordner** > **Katalog**), bevor Sie ein Adobe Stock-Bild hochladen.
Löschen Sie hochgeladene Adobe Stock-Bilder aus den `pub/media`- und `pub/media/catalog`-Ordnern im Adobe Commerce-Dateisystem und laden Sie Bilder stattdessen in alle zulässigen Unterverzeichnisse des Media Gallery-Speicherstamms hoch (**Speicherstamm** > **Katalog**).

## Verwandtes Lesen

* [Media Storage](https://experienceleague.adobe.com/de/docs/commerce-admin/content-design/wysiwyg/storage/media-storage) in unserem Benutzerhandbuch.
