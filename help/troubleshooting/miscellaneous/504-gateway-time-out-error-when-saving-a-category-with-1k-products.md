---
title: 504 Gateway-Zeitüberschreitungsfehler beim Speichern einer Kategorie mit 1k+ Produkten
description: In diesem Artikel wird eine Lösung für das Problem mit der Zeitüberschreitung vorgeschlagen, das bei der Ausführung von Vorgängen mit großen Kategorien (1 k+ Produkte) auftreten kann.
exl-id: 1f4b0385-215d-4d3d-8704-986c090824aa
feature: Cache, Categories, Marketing Tools, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# 504 Gateway-Zeitüberschreitungsfehler beim Speichern einer Kategorie mit 1k+ Produkten

In diesem Artikel wird eine Lösung für das Problem mit der Zeitüberschreitung vorgeschlagen, das bei der Ausführung von Vorgängen mit großen Kategorien (1 k+ Produkte) auftreten kann.

## Betroffene Produkte und Versionen:

* Adobe Commerce auf Cloud-Infrastruktur 2.3.3
* Adobe Commerce vor Ort 2.3.3
* Magento Open Source 2.3.3

## Problem

Voraussetzungen: Die **Stores** > **Konfiguration** > **KATALOG** > **Katalog** > **Kategoriepfad für Produkt-URLs verwenden** ist auf *Ja* für Ihre Store-Ansicht.

<u>Zu reproduzierende Schritte</u>

1. Navigieren Sie im Commerce-Admin zu **Katalog** > **Kategorien**.
1. Öffnen Sie eine große Kategorie, z. B. mehr als 1000 zugewiesene Produkte.
1. Fügen Sie der Kategorie ein Produkt hinzu.
1. Klicks **Kategorie speichern**.

<u>Erwartetes Ergebnis:</u>

Die Kategorie wurde erfolgreich gespeichert.

<u>Ergebnis:</u>

Nach fünf Minuten Speichervorgang wird die Fehlerseite 504 Gateway Timeout angezeigt.

## Ursache

Der Prozess dauert länger als der konfigurierte Timeout des Servers.

## Lösung

Deaktivieren der **URL-Neuschreibungen für &quot;Kategorie/Produkt&quot;generieren** entfernt alle Kategorie-/Produkt-URL-Neuschreibungen aus der Datenbank und verringert die für Vorgänge mit großen Kategorien erforderliche Zeit erheblich.

>[!WARNING]
>
>Wenn Sie diese Option deaktivieren, werden Kategorie-/Produkt-URL-Neuschreibungen dauerhaft entfernt, ohne dass eine Wiederherstellung möglich ist.

So deaktivieren Sie die **URL-Neuschreibungen für &quot;Kategorie/Produkt&quot;generieren** Option:

1. Navigieren Sie in Commerce Admin zu **Stores** > **Konfiguration** > **KATALOG** > **Katalog**.
1. In der oberen linken Ecke der Konfigurationsseite finden Sie im **Anwendungsbereich** -Feld, legen Sie den Konfigurationsbereich auf *Standardkonfiguration*.
1. Satz **URL-Neuschreibungen für &quot;Kategorie/Produkt&quot;generieren** nach *Nein*.
1. Klicks **Konfiguration speichern**.
1. Cache bereinigen durch Ausführen    ```bash    bin/magento cache:clean    ```    oder im Commerce Admin unter **System** > **Instrumente** > **Cacheverwaltung**.

Jetzt können Sie Produkte zu Kategorien hinzufügen oder Kategorien mit einer großen Anzahl von Produkten verschieben. Diese Vorgänge werden viel weniger Zeit in Anspruch nehmen und sollten keinen Timeout verursachen.

## Verwandtes Lesen

[Automatische Produktumleitungen](https://docs.magento.com/user-guide/v2.3/marketing/url-redirect-product-automatic.html) in unserem Benutzerhandbuch.
