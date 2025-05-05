---
title: 504 Gateway-Zeitüberschreitungsfehler beim Speichern einer Kategorie mit 1K+-Produkten
description: In diesem Artikel wird eine Lösung für das Zeitüberschreitungsproblem vorgeschlagen, das bei der Durchführung von Vorgängen mit großen Kategorien (1k+ plus Produkte) auftreten kann.
exl-id: 1f4b0385-215d-4d3d-8704-986c090824aa
feature: Cache, Categories, Marketing Tools, Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# 504 Gateway-Zeitüberschreitungsfehler beim Speichern einer Kategorie mit 1K+-Produkten

In diesem Artikel wird eine Lösung für das Zeitüberschreitungsproblem vorgeschlagen, das bei der Durchführung von Vorgängen mit großen Kategorien (1k+ plus Produkte) auftreten kann.

## Betroffene Produkte und Versionen:

* Adobe Commerce auf Cloud-Infrastruktur 2.3.3
* Adobe Commerce On-Premises 2.3.3
* Magento Open Source 2.3.3

## Problem

Voraussetzungen: Die Option **Stores** > **Configuration** > **CATALOG** > **CATALOG** > **Verwenden des Kategorienpfads für Produkt-URLs** ist für Ihre Store-Ansicht auf *Yes* festgelegt.

<u>Schritte zur Reproduktion</u>

1. Wechseln Sie in der Commerce-Admin zu **Katalog** > **Kategorien**.
1. Öffnen Sie eine große Kategorie, z. B. mehr als 1000 zugewiesene Produkte.
1. Fügen Sie der Kategorie ein Produkt hinzu.
1. Klicken Sie **Kategorie speichern**.

<u>Erwartetes Ergebnis:</u>

Kategorie wurde gespeichert.

<u>Tatsächliches Ergebnis:</u>

Nach fünf Minuten des Speichervorgangs wird die Fehlerseite 504 Gateway Timeout angezeigt.

## Ursache

Der Prozess dauert länger als die konfigurierte Zeitüberschreitung des Servers.

## Lösung

Wenn Sie die Option **Neuschreibungen der Kategorie-/Produkt-URL generieren** deaktivieren, werden alle Neuschreibungen der Kategorie-/Produkt-URLs aus der Datenbank entfernt, was die Zeit für die Vorgänge mit großen Kategorien erheblich verkürzt.

>[!WARNING]
>
>Wenn Sie diese Option deaktivieren, werden die Neuschreibungen der Kategorie-/Produkt-URLs dauerhaft entfernt, ohne dass sie wiederhergestellt werden können.

So deaktivieren Sie **Option „URL-Neuschreibungen für Kategorie/Produkt**&quot;:

1. Navigieren Sie in der Commerce Admin zu **Stores** > **Configuration** > **CATALOG** > **CATALOG**.
1. Legen Sie oben links auf der Konfigurationsseite im Feld **Umfang** Ihren Konfigurationsbereich auf &quot;*&quot;*.
1. Setzen **„Kategorie-/Produkt-URL-Neuschreibungen generieren** auf *Nein*.
1. Klicken Sie **Konfiguration speichern**.
1. Cache durch Ausführen von bereinigen    ```bash    bin/magento cache:clean    ```    oder in der Commerce Admin unter **System** > **Tools** > **Cache-Verwaltung**.

Jetzt können Sie mit dem Hinzufügen von Produkten zu Kategorien oder dem Verschieben von Kategorien mit einer großen Anzahl von Produkten fortfahren. Diese Vorgänge benötigen viel weniger Zeit und sollten keine Zeitüberschreitung verursachen.

## Verwandtes Lesen

[Automatische Produktweiterleitungen](https://experienceleague.adobe.com/de/docs/commerce-admin/marketing/seo/url-rewrites/url-redirect-product-automatic) in unserem Benutzerhandbuch.
