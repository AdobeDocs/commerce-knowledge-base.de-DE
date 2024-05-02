---
title: "Bekanntes Problem mit Adobe Commerce 2.4.0: Klarna On-Site Messaging - leere Seiten"
description: In diesem Artikel wird ein bekanntes Adobe Commerce 2.4.0-Problem mit der Zahlungsmethode Klarna beschrieben, bei dem die Aktivierung von Klarna On-site-Messaging ohne Angabe eines Designthemas dazu führt, dass Produktseiten auf der Storefront nicht korrekt angezeigt werden (Produktseiten erscheinen leer).
exl-id: f0f9edfc-eaad-4947-9200-41e217bfbe84
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Bekanntes Problem mit Adobe Commerce 2.4.0: Klarna On-Site Messaging - leere Seiten

In diesem Artikel wird ein bekanntes Adobe Commerce 2.4.0-Problem mit der Zahlungsmethode Klarna beschrieben, bei dem die Aktivierung von Klarna On-site-Messaging ohne Angabe eines Designthemas dazu führt, dass Produktseiten auf der Storefront nicht korrekt angezeigt werden (Produktseiten erscheinen leer).

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort 2.4.0
* Adobe Commerce auf Cloud-Infrastruktur 2.4.0

<u>Voraussetzungen:</u> Die Zahlungsmethode Klarna ist aktiviert.

<u>Zu reproduzierende Schritte:</u>

1. Navigieren Sie im Commerce-Admin zu **Stores** > **Konfiguration** > **Vertrieb** > **Zahlungsmethoden** > **Klarna** > **Klarna On-site Messaging**.
1. Satz **Aktivieren** nach *Ja*.
1. Lassen Sie die **Design-Design** Feld leer.
1. Konfiguration speichern durch Klicken auf **Konfiguration speichern**.
1. Gehen Sie zur Storefront und navigieren Sie zu einer beliebigen Produktseite.

<u>Erwartetes Ergebnis:</u>

Die Seite wurde erfolgreich geladen, wobei das Standarddesign-Design für Klarna-On-site-Nachrichten angewendet wurde.

<u>Ergebnis:</u>

Eine leere Seite wird angezeigt.

## Lösung

Wenn Sie die On-site-Nachrichten von Klarna aktivieren, stellen Sie immer sicher, dass die Variable **Design-Design** -Feld nicht leer ist.
