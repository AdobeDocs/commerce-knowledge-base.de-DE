---
title: Fehler beim Bereinigen des Cache in Commerce Admin
description: 'In diesem Artikel wird erläutert, wie Sie die Ursache einer Fehlermeldung identifizieren können, die beim Löschen des Caches in Commerce Admin auftritt. Wenn Sie versuchen, den Cache über den Admin zu bereinigen, erhalten Sie die folgende Nachricht:'
exl-id: aa414e04-bc6d-46bd-b98f-0446b97bda14
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# Fehler beim Bereinigen des Cache in Commerce Admin

In diesem Artikel wird erläutert, wie Sie die Ursache einer Fehlermeldung identifizieren können, die beim Löschen des Caches in Commerce Admin auftritt. Wenn Sie versuchen, den Cache über den Admin zu bereinigen, erhalten Sie die folgende Nachricht:
Die Datei &quot;*/app/project-id/pub/media/catalog/product/cache/directory/filename&quot;kann nicht gelöscht werden. Warnung!unlink(/app/project id/pub/media/catalog/product/cache/directory/filename): Keine solche Datei oder Verzeichnis*

## Betroffene Produkte und Versionen

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0-2.3.7, 2.4.0-2.4.2-p1

## Problem

Wenn Sie versuchen, den Cache über den Admin zu leeren, erhalten Sie eine Fehlermeldung.

<u>Zu reproduzierende Schritte:</u>

1. Wechseln Sie im Admin zu **System** > **Tools** > **Cache-Verwaltung**.
1. Wählen Sie eine der klaren Zwischenspeicheroptionen aus.

<u>Erwartetes Ergebnis:</u>

Der Adobe Commerce-Cache wurde ohne Fehler geleert.

<u>Tatsächliches Ergebnis:</u>

Sie erhalten den Fehler &quot;Datei kann nicht gelöscht werden&quot;.

## Ursache

Der Fehler bezieht sich auf eine Verzögerung zwischen dem Zeitpunkt, zu dem der Cache-Bereinigungsvorgang initiiert wurde, und dem Zeitpunkt, zu dem er als abgeschlossen gemeldet wurde.

## Lösung

1. Vergewissern Sie sich, dass die im Fehler genannten Dateien nicht auf dem Server vorhanden sind (überprüfen Sie, ob die Cache-Bereinigung erfolgreich war):

```bash
ls -la pub/media/catalog/product/cache/directory/filename
```

Wenn die folgende Ausgabe angezeigt wird:

```bash
ls: cannot access 'pub/media/catalog/product/cache/directory/filename/': No such file or directory
```

Es wurde versucht, die Dateien zu löschen, nachdem der Vorgang bereits abgeschlossen war. Dies ist kein Fehler; es handelt sich um ein Messaging-Problem bei gleichzeitigen Vorgängen, das manchmal auftreten wird. Es gibt kein Problem zur Fehlerbehebung.
Wenn die Ausgabe jedoch zeigt, dass sich die Dateien noch im Cache befinden, müssen Sie [ein Support-Ticket senden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Verwandte Informationen

* [Cache-Verwaltung](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management) in unserer Entwicklerdokumentation.
