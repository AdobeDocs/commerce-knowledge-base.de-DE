---
title: Fehler beim Bereinigen des Caches in Commerce Admin
description: 'In diesem Artikel wird erläutert, wie Sie die Ursache einer Fehlermeldung ermitteln, die beim Bereinigen des Caches im Commerce Admin-Bereich auftritt. Wenn Sie versuchen, den Cache über die Admin zu bereinigen, erhalten Sie die folgende Nachricht:'
exl-id: aa414e04-bc6d-46bd-b98f-0446b97bda14
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# Fehler beim Bereinigen des Caches in Commerce Admin

In diesem Artikel wird erläutert, wie Sie die Ursache einer Fehlermeldung ermitteln, die beim Bereinigen des Caches im Commerce Admin-Bereich auftritt. Wenn Sie versuchen, den Cache über die Admin zu bereinigen, erhalten Sie die folgende Nachricht:
*/app/project-id/pub/media/catalog/product/cache/directory/filename“-Datei kann nicht gelöscht werden. Warnung!unlink(/app/project id/pub/media/catalog/product/cache/directory/filename): Keine solche Datei oder kein solches Verzeichnis*

## Betroffene Produkte und Versionen

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0-2.3.7, 2.4.0-2.4.2-p1

## Problem

Wenn Sie versuchen, den Cache über den Administrator zu bereinigen, erhalten Sie eine Fehlermeldung.

<u>Schritte zur Reproduktion:</u>

1. Gehen Sie in der Admin zu **System** > **Tools** > **Cache-Verwaltung**.
1. Wählen Sie eine der leeren Zwischenspeicherungsoptionen aus.

<u>Erwartetes Ergebnis:</u>

Sie haben den Adobe Commerce-Cache erfolgreich und fehlerfrei geleert.

<u>Tatsächliches Ergebnis:</u>

Sie erhalten die Fehlermeldung „Datei kann nicht gelöscht werden“.

## Ursache

Der Fehler bezieht sich auf eine Verzögerung zwischen dem Zeitpunkt, zu dem der Cache-Bereinigungsvorgang gestartet wurde, und dem Zeitpunkt, zu dem er als abgeschlossen gemeldet wurde.

## Lösung

1. Vergewissern Sie sich, dass die im Fehler genannten Dateien nicht auf dem Server vorhanden sind (und überprüfen Sie, ob die Cache-Bereinigung erfolgreich war):

```bash
ls -la pub/media/catalog/product/cache/directory/filename
```

Wenn die folgende Ausgabe angezeigt wird:

```bash
ls: cannot access 'pub/media/catalog/product/cache/directory/filename/': No such file or directory
```

Es wurde versucht, die Dateien zu löschen, als der Vorgang bereits abgeschlossen war. Dies ist kein Fehler, sondern ein Problem mit gleichzeitigem Messaging, das gelegentlich auftreten dürfte. Es gibt kein Problem zur Fehlerbehebung.
Wenn die Ausgabe jedoch zeigt, dass sich die Dateien noch im Cache befinden, müssen Sie [ein Support-Ticket senden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Verwandtes Lesen

* [Cache-Verwaltung](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/tools/cache-management) in unserer Entwicklerdokumentation.
