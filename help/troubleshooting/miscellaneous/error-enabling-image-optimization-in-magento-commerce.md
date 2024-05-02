---
title: Fehler beim Aktivieren der Bildoptimierung in Adobe Commerce
description: Dieser Artikel bietet eine Lösung für das Problem, bei dem die Fastly Image Optimization (IO) standardmäßig deaktiviert ist, mit einer Benachrichtigung, um Fastly zu kontaktieren, um die Bildoptimierung zu aktivieren. (Der Fastly Cloud Image Optimizer ist ein Echtzeit-Bildbearbeitungs- und -optimierungsdienst, der die Bildbereitstellung durch Bereitstellung bandbreiteneffizienter Bilder beschleunigt.)
exl-id: 7b64c786-3c74-4642-b0d0-15b5648163a0
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# Fehler beim Aktivieren der Bildoptimierung in Adobe Commerce

Dieser Artikel bietet eine Lösung für das Problem, bei dem die Fastly Image Optimization (IO) standardmäßig deaktiviert ist, mit einer Benachrichtigung, um Fastly zu kontaktieren, um die Bildoptimierung zu aktivieren. (Der Fastly Cloud Image Optimizer ist ein Echtzeit-Bildbearbeitungs- und -optimierungsdienst, der die Bildbereitstellung durch Bereitstellung bandbreiteneffizienter Bilder beschleunigt.)

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur 2.2.x, 2.3.x

## Problem

Auf der Seite Schnelle Konfiguration neben dem Fastly I/O-Snippet sehen Sie den aktuellen Status: \_disabled \_with der folgenden Meldung darunter: Wenden Sie sich an Ihren Vertriebsmitarbeiter oder senden Sie eine E-Mail an `support@fastly.com` , um die Aktivierung der Bildoptimierung für Ihren Fastly-Service anzufordern.

## Ursache

Die Site ist möglicherweise noch nicht live. Es gibt Prozesse zum Vorausfüllen der Site, wenn sie in der Fastly-Datenbank live geschaltet wird.

## Lösung

Erstellen Sie eine [Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) und Bildoptimierung anfordern.
