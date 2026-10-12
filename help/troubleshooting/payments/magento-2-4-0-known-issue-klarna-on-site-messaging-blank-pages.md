---
title: 'Bekanntes Problem in Adobe Commerce 2.4.0: Klarna Seiten zum Messaging vor Ort leer'
description: Dieser Artikel beschreibt ein bekanntes Adobe Commerce 2.4.0 Problem mit der Bezahlmethode Klarna, bei dem die Aktivierung von Klarna-Onsite-Messaging ohne Angabe eines Design-Designs dazu führt, dass Produktseiten in der Storefront nicht korrekt angezeigt werden (Produktseiten erscheinen leer).
exl-id: f0f9edfc-eaad-4947-9200-41e217bfbe84
feature: Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '204'
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
