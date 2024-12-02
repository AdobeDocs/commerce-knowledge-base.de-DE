---
title: 'Adobe Commerce 2.4.2-p1: Rechnungsschein mit falschem Wert'
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

1. Erstellen Sie ein **Kundenkonto testen** und fügen Sie es zur **Einzelhandelsgruppe** hinzu.
1. Erstellen Sie eine **neue Bestellung** für den Testkunden, fügen Sie **Produkt** und **Adresse** hinzu.
1. Wählen Sie **Versandmethode** aus.
1. Ändern Sie im Abschnitt **Kontoinformationen** die Kundengruppe von **Händler** in **Regierung**.
1. Klicken Sie auf **Bestellung platzieren**.
1. Klicken Sie auf **Rechnung** > **Rechnung senden**.

<u>Erwartete Ergebnisse</u>:

Der folgende Hinweis sollte unter dem Abschnitt **Hinweise für diese Bestellung** angezeigt werden: &quot;Vertex Invoice erfolgreich gesendet. Betrag: 0,00 USD.&quot;

<u>Tatsächliche Ergebnisse</u>:

Der folgende Hinweis wird unter dem Abschnitt **Hinweise für diese Bestellung** angezeigt: &quot;Vertex Invoice erfolgreich gesendet. Betrag: 3,23 USD.&quot;

## Lösung

Dieses Problem wurde in Version 2.4.3 behoben.
