---
title: Nicht angezeigte Lagerbilder, Adobe Commerce und Magento Open Source 2.3.7-p2
description: Dieser Artikel bietet eine Lösung für das Problem, dass Adobe-Stock-Bilder, die in die Dateisystemverzeichnisse "pub/media"oder "pub/media/catalog"hochgeladen wurden, nicht in der Benutzeroberfläche der Media Gallery angezeigt werden. Dies liegt daran, dass sich die Bilder außerhalb der zulässigen Medien-Galerie-Verzeichnisse befinden. Damit diese Bilder Händler anzeigen können, müssen Sie die Bilder im Dateisystem löschen und erneut in ein zulässiges Verzeichnis der Media Gallery hochladen.
exl-id: 84488d87-095f-4739-858f-19a52d6e5822
feature: Categories, Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# Nicht angezeigte Lagerbilder, Adobe Commerce und Magento Open Source 2.3.7-p2

Dieser Artikel bietet eine Lösung für das Problem, dass Adobe-Stock-Bilder in die Dateisystemverzeichnisse hochgeladen werden. `pub/media` oder `pub/media/catalog` werden nicht in der Benutzeroberfläche der Media Gallery angezeigt. Dies liegt daran, dass sich die Bilder außerhalb der zulässigen Medien-Galerie-Verzeichnisse befinden. Damit diese Bilder Händler anzeigen können, müssen Sie die Bilder im Dateisystem löschen und erneut in ein zulässiges Verzeichnis der Media Gallery hochladen.

## Betroffene Produkte und Versionen

* Adobe Commerce und Magento Open Source 2.3.7-p2


## Problem

Händler können Adobe Stock-Bilder in den Speicherstamm in der Media Gallery hochladen. Diese Bilder werden jedoch nicht in der Benutzeroberfläche angezeigt und erscheinen so, als wären sie nicht hochgeladen worden. Dies liegt daran, dass das System erkennt, dass das Bild bereits in das Dateisystem hochgeladen wurde, obwohl es nicht in der Benutzeroberfläche von Media Gallery verfügbar ist. Das bedeutet, dass ein Händler ein Bild in `pub/media` oder `pub/media/catalog`, können sie dieses Bild erst verwenden, wenn es direkt im Dateisystem gelöscht wird.

<u>Zu reproduzierende Schritte</u>

1. Aktivieren Sie Adobe Stock mit gültigen API-Schlüsseln.
1. Offene Mediengalerie (**Katalog** > **Kategorien** > **Inhalt** Abschnitt > Klicken **Aus Galerie auswählen**).
1. Klicks **Adobe Stock durchsuchen**.
1. Wählen Sie ein Bild. Klicken **Vorschau speichern**. Beachten Sie, dass Sie möglicherweise das Adobe Stock-Raster zurücksetzen müssen, damit Bilder angezeigt werden.

<u>Erwartetes Ergebnis</u>:

Das Bild wird angezeigt.

<u>Tatsächliches Ergebnis</u>:

Eine Fehlermeldung wird angezeigt: *Das Bild kann nicht gefunden werden. Wir können dieses Bild nicht in der Mediengalerie finden.*

## Ursache

Bilder können über Adobe Stock in den Speicherstamm der Media Gallery hochgeladen werden.

## Lösung

Wählen Sie ein beliebiges Unterverzeichnis des Speicherstamms der Mediengalerie aus (außer **Speicherstamm** > **Katalog**), bevor Sie ein Adobe Stock-Bild hochladen.
Löschen Sie die hochgeladenen Adobe Stock-Bilder aus dem `pub/media` und `pub/media/catalog` Ordner im Adobe Commerce-Dateisystem und laden Bilder stattdessen in alle zulässigen Medien-Galerie-Stammordner-Unterverzeichnisse hoch (außer **Speicherstamm** > **Katalog**).

## Verwandtes Lesen

* [Medienspeicher](https://docs.magento.com/user-guide/v2.3/cms/media-storage.html) in unserem Benutzerhandbuch.
