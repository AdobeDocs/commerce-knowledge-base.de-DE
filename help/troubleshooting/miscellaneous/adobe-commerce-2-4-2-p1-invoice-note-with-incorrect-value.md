---
title: "Adobe Commerce 2.4.2-p1: Rechnungsschein mit falschem Wert"
description: In diesem Artikel wird ein bekanntes Adobe Commerce 2.4.2-p1-Problem beschrieben, bei dem eine Rechnungsnote mit einem falschen Wert generiert wird, wenn die Kundengruppe beim Erstellen der Bestellung geändert wird. Dieses Problem wurde in Version 2.4.3 behoben.
exl-id: bde90251-625f-4c9d-8e5a-9a2019656125
feature: Customer Service, Invoices
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Adobe Commerce 2.4.2-p1: Rechnungsschein mit falschem Wert

In diesem Artikel wird ein bekanntes Adobe Commerce 2.4.2-p1-Problem beschrieben, bei dem eine Rechnungsnote mit einem falschen Wert generiert wird, wenn die Kundengruppe beim Erstellen der Bestellung geändert wird. Dieses Problem wurde in Version 2.4.3 behoben.

## Betroffene Produkte und Versionen

* Adobe Commerce vor Ort 2.4.2-p1
* Adobe Commerce auf Cloud-Infrastruktur 2.4.2-p1

## Problem

Wenn die Kundengruppe zum Zeitpunkt der Bestellerstellung geändert wird, wird die Rechnung mit einem falschen Rechnungsschein generiert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine **Kundenkonto testen** und fügen Sie sie zum **Einzelhandelskundengruppe**.
1. Erstellen Sie eine **Neue Bestellung** Fügen Sie für den Testkunden **Produkt** und **Adresse**.
1. Auswählen **Versandmethode**.
1. Im **Kontoinformationen** Abschnitt Kundengruppe ändern von **Einzelhändler** nach **Regierung**.
1. Klicks **Bestellung platzieren**.
1. Klicks **Rechnung** > **Submit Invoice**.

<u>Erwartete Ergebnisse</u>:

Die folgende Anmerkung sollte unter der **Hinweise zu dieser Reihenfolge**  Abschnitt: &quot;Vertex Invoice erfolgreich gesendet. Betrag: 0,00 USD.&quot;

<u>Tatsächliche Ergebnisse</u>:

Die folgende Anmerkung wird unter der **Hinweise zu dieser Reihenfolge** Abschnitt: &quot;Vertex Invoice erfolgreich gesendet. Betrag: 3,23 USD.&quot;

## Lösung

Dieses Problem wurde in Version 2.4.3 behoben.
