---
title: 'Bekanntes Problem in Adobe Commerce 2.4.0: Klarna Seiten zum Messaging vor Ort leer'
description: Dieser Artikel beschreibt ein bekanntes Adobe Commerce 2.4.0 Problem mit der Bezahlmethode Klarna, bei dem die Aktivierung von Klarna-Onsite-Messaging ohne Angabe eines Design-Designs dazu führt, dass Produktseiten in der Storefront nicht korrekt angezeigt werden (Produktseiten erscheinen leer).
exl-id: f0f9edfc-eaad-4947-9200-41e217bfbe84
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Bekanntes Problem in Adobe Commerce 2.4.0: Klarna Seiten zum Messaging vor Ort leer

Dieser Artikel beschreibt ein bekanntes Adobe Commerce 2.4.0 Problem mit der Bezahlmethode Klarna, bei dem die Aktivierung von Klarna-Onsite-Messaging ohne Angabe eines Design-Designs dazu führt, dass Produktseiten in der Storefront nicht korrekt angezeigt werden (Produktseiten erscheinen leer).

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises 2.4.0
* Adobe Commerce auf Cloud-Infrastruktur 2.4.0

<u>Voraussetzungen: </u> Zahlungsmethode Klarna ist aktiviert.

<u>Schritte zur Reproduktion:</u>

1. Wechseln Sie in Commerce Admin zu **Stores** > **Configuration** > **Sales** > **Zahlungsmethoden** > **Klarna** > **Klarna On-Site Messaging**.
1. Setzen Sie **Aktivieren** auf *Ja*.
1. Lassen Sie das Feld **Design** leer.
1. Speichern Sie die Konfiguration, indem **Konfiguration speichern** klicken.
1. Gehen Sie zu Storefront und navigieren Sie zu einer beliebigen Produktseite.

<u>Erwartetes Ergebnis:</u>

Die Seite wird mit dem für Klarna-Messaging vor Ort angewendeten Standard-Design erfolgreich geladen.

<u>Tatsächliches Ergebnis:</u>

Eine leere Seite wird angezeigt.

## Lösung

Wenn Sie das Klarna-Messaging vor Ort aktivieren, stellen Sie immer sicher, dass das Feld **Design** nicht leer ist.
