---
title: 504 Gateway-Zeitüberschreitungsfehler beim Speichern einer Kategorie mit 1k+ Produkten
description: In diesem Artikel wird eine Lösung für das Problem mit der Zeitüberschreitung vorgeschlagen, das bei der Ausführung von Vorgängen mit großen Kategorien (1 k+ Produkte) auftreten kann.
exl-id: 1f4b0385-215d-4d3d-8704-986c090824aa
feature: Cache, Categories, Marketing Tools, Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

Voraussetzungen: Die Option **Stores** > **Konfiguration** > **KATALOG** > **Katalog** > **Kategoriepfad für Produkt-URLs verwenden** ist für Ihre Store-Ansicht auf *Ja* eingestellt.

<u>Zu reproduzierende Schritte</u>

1. Navigieren Sie im Commerce Admin zu **Katalog** > **Kategorien**.
1. Öffnen Sie eine große Kategorie, z. B. mehr als 1000 zugewiesene Produkte.
1. Fügen Sie der Kategorie ein Produkt hinzu.
1. Klicken Sie auf **Kategorie speichern**.

<u>Erwartetes Ergebnis:</u>

Die Kategorie wurde erfolgreich gespeichert.

<u>Tatsächliches Ergebnis:</u>

Nach fünf Minuten Speichervorgang wird die Fehlerseite 504 Gateway Timeout angezeigt.

## Ursache

Der Prozess dauert länger als der konfigurierte Timeout des Servers.

## Lösung

Durch Deaktivieren der Option **URL-Neuschreibungen für Kategorie/Produkt generieren** werden alle Kategorie-/Produkt-URL-Neuschreibungen aus der Datenbank entfernt und die für Vorgänge mit großen Kategorien erforderliche Zeit erheblich verringert.

>[!WARNING]
>
>Wenn Sie diese Option deaktivieren, werden Kategorie-/Produkt-URL-Neuschreibungen dauerhaft entfernt, ohne dass eine Wiederherstellung möglich ist.

So deaktivieren Sie die Option **URL-Neuschreibungen für Kategorie/Produkt generieren**:

1. Navigieren Sie im Commerce-Admin zu &quot;**Stores**&quot;> &quot;**Konfiguration**&quot;> &quot;**KATALOG**&quot;> &quot;**Katalog**&quot;.
1. Legen Sie in der oberen linken Ecke der Konfigurationsseite im Feld **Umfang** den Konfigurationsbereich auf *Standardkonfiguration* fest.
1. Setzen Sie **URL &quot;Kategorie/Produkt&quot;generieren, schreibt** neu auf *Nein*.
1. Klicken Sie auf **Konfiguration speichern**.
1. Cache bereinigen durch Ausführen    ```bash    bin/magento cache:clean    ```    oder im Commerce Admin unter **System** > **Tools** > **Cache-Verwaltung**.

Jetzt können Sie Produkte zu Kategorien hinzufügen oder Kategorien mit einer großen Anzahl von Produkten verschieben. Diese Vorgänge werden viel weniger Zeit in Anspruch nehmen und sollten keinen Timeout verursachen.

## Verwandtes Lesen

[Automatische Produktumleitungen](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/seo/url-rewrites/url-redirect-product-automatic) in unserem Benutzerhandbuch.
