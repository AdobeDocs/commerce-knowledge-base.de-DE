---
title: 'Adobe Commerce 2.4.2-P1: Rechnungsnachweis mit falschem Wert'
description: In diesem Artikel wird ein bekanntes Adobe Commerce 2.4.2-p1-Problem beschrieben, bei dem ein Rechnungsnachweis mit einem falschen Wert generiert wird, wenn die Kundengruppe beim Erstellen der Bestellung geändert wird. Dieses Problem wurde in Version 2.4.3 behoben.
exl-id: bde90251-625f-4c9d-8e5a-9a2019656125
feature: Customer Service, Invoices
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 591c578b-908e-5b79-a9d3-931dfe60c24c
    internal-label: Invoices
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
subfeature_v2:
  - id: deedbb4d-f1b7-58ea-a34a-de1f481f9d4c
    internal-label: Customer Service
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%
---
# Adobe Commerce 2.4.2-P1: Rechnungsnachweis mit falschem Wert

In diesem Artikel wird ein bekanntes Adobe Commerce 2.4.2-p1-Problem beschrieben, bei dem ein Rechnungsnachweis mit einem falschen Wert generiert wird, wenn die Kundengruppe beim Erstellen der Bestellung geändert wird. Dieses Problem wurde in Version 2.4.3 behoben.

## Betroffene Produkte und Versionen

* Adobe Commerce On-Premises 2.4.2-p1
* Adobe Commerce auf Cloud-Infrastruktur 2.4.2-p1

## Problem

Wenn die Kundengruppe zum Zeitpunkt der Auftragserstellung geändert wird, wird die Rechnung mit einer falschen Rechnungsnotiz erstellt.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie **Testkundenkonto** und fügen Sie es der **Einzelhandelskundengruppe“**.
1. Erstellen Sie eine **Neue Bestellung** für den Testkunden und fügen Sie **Produkt** und **Adresse** hinzu.
1. Wählen Sie **Versandart**.
1. Ändern Sie im Abschnitt **Kontoinformationen** die Kundengruppe von **Retailer** zu **Government**.
1. Klicken Sie **Bestellung aufgeben**.
1. Klicken Sie **Rechnung** > **Rechnung senden**.

<u>Erwartete Ergebnisse</u>:

Der folgende Hinweis sollte unter dem Abschnitt **Hinweise für diese Bestellung** erscheinen: „Vertex Rechnung erfolgreich gesendet. Betrag: $0.00.“

<u>Tatsächliche Ergebnisse</u>:

Unter dem Abschnitt &quot;**für diese Bestellung“ wird** Hinweis angezeigt: „Vertex Rechnung erfolgreich gesendet. Betrag: 3,23 $.“

## Lösung

Dieses Problem wurde in Version 2.4.3 behoben.
