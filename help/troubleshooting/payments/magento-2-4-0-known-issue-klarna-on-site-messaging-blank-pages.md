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

1. Navigieren Sie im Commerce-Admin zu &quot;**Stores**&quot;> &quot;**Konfiguration**&quot;> &quot;**Verkauf**&quot;> &quot;**Zahlungsmethoden**&quot;> &quot;**Klarna**&quot;> &quot;**Klarna On-Site Messaging**&quot;.
1. Setzen Sie **Enable** auf *Yes*.
1. Lassen Sie das Feld **Design theme** leer.
1. Speichern Sie die Konfiguration durch Klicken auf **Konfiguration speichern**.
1. Gehen Sie zur Storefront und navigieren Sie zu einer beliebigen Produktseite.

<u>Erwartetes Ergebnis:</u>

Die Seite wurde erfolgreich geladen, wobei das Standarddesign-Design für Klarna-On-site-Nachrichten angewendet wurde.

<u>Tatsächliches Ergebnis:</u>

Eine leere Seite wird angezeigt.

## Lösung

Wenn Sie die On-site-Benachrichtigung von Klarna aktivieren, stellen Sie sicher, dass das Feld **Design theme** nicht leer ist.
