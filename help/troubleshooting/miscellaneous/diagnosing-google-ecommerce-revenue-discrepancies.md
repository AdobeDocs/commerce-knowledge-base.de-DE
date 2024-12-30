---
title: Diagnose von Diskrepanzen beim E-Commerce-Umsatz mit Google
description: 'Dieser Artikel enthält Lösungen für Diskrepanzen zwischen Google und Magento Business Intelligence (MBI). Das E-Commerce-Tracking von Google unterstützt sowohl Ihr Google Analytics-Konto als auch Ihre MBI-Dashboards, aber es führt dazu, dass uns viele Kunden fragen: Sollten beide Tools dieselbe Menge an **Bestellungen** und **Umsatz**?'
exl-id: b2e43e70-d234-4338-ae81-fa401416be5a
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 0%

---

# Diagnose von Diskrepanzen beim E-Commerce-Umsatz mit Google

Dieser Artikel enthält Lösungen für Diskrepanzen zwischen Google und Magento Business Intelligence (MBI). Das E-Commerce-Tracking von Google bietet Ihnen eine leistungsstarke Funktion sowohl für Ihr Google Analytics-Konto als auch für Ihre MBI-Dashboards, aber es führt dazu, dass uns viele Kunden fragen: Sollten beide Tools die gleiche Anzahl an **Bestellungen** und **Umsatz** melden?

Nach unserer Erfahrung lautet die Antwort „nein“ in fast allen Fällen. Dies liegt daran, dass das Google eCommerce-Tracking die Bestellinformationen während eines Schaltflächen-Klickereignisses auf Ihrer Website erhält, bei dem viele Bestellungsattribute fehlen, die später in Ihrer Datenbank aufgezeichnet wurden - alles von nicht registrierten Bestellungen bis hin zu einer späteren Stornierung oder Rückerstattung.

Wir wissen, dass eine Diskrepanz zwischen Google und MBI zu Unsicherheit für Sie und Ihr Team führen kann. Wir möchten Ihnen dabei helfen, den Unterschied zwischen diesen beiden Zahlen zu verstehen, der möglicherweise Anpassungen in Ihrem Google-Konto oder in Ihrer Datenbank erforderlich macht.

## Warum meldet GA **weniger** Umsatz als meine Datenbank?

Wenn Google Analytics nicht alle Bestellungen und Umsätze erfassen, ist das ein Hinweis darauf, dass nicht alle Bestellungen auf Ihrer Website erfasst werden. Da Sie wissen, dass Ihre Datenbankdaten die endgültige Zahl sind, können Sie einige Schritte ausführen, um die Grundursache zu ermitteln - und möglicherweise Google dabei helfen, weitere Informationen zu erfassen.

* Das E-Commerce-Tracking in Google war nicht immer aktiviert. Schauen Sie sich einen kleineren, neueren Zeitraum an.
* Ihr Google eCommerce-Tracking ist nicht so eingerichtet, dass Käufe von bestimmten Browsern, Betriebssystemen oder Geräten erfasst werden.
* Das Klickereignis, das mit Ihrem Google eCommerce-Tracking verbunden ist, verfolgt Steuern, Versandkosten oder andere Gebühren, die über der Bestellsumme liegen, nicht korrekt.
* Ihr Datenbank-Zeitstempel befindet sich in einer anderen Zeitzone als Ihr Google Analytics-Zeitstempel.
* Personen können Ihre Website über Inkognito-Fenster oder mit ausgeschalteten Cookies besuchen.

## Warum meldet GA **mehr** Umsatz als meine Datenbank?

Wir haben herausgefunden, dass es für Google Analytics üblicher ist, Bestellungen und Umsätze zu oft zu melden als für E-Commerce-Datenbanken. Das ist nicht immer schlecht. Ihre Datenbank ist die endgültige Aufzeichnung der Transaktionen, die auf Ihrer Website durchgeführt wurden, und es gibt mehrere Gründe, warum Google hoch sein könnte, auch wenn Sie es perfekt eingerichtet haben:

* Beim E-Commerce-Tracking werden doppelte Schaltflächen-Klicks erfasst, die nur als eine Bestellung in Ihrer Datenbank registriert werden.
* Sie haben eine hohe Anzahl von stornierten, zurückerstatteten oder betrügerischen Bestellungen. Dies ist eine Statusänderung, die geschieht, nachdem E-Commerce die Daten nachverfolgt.
* Die Metriken **Umsatz** und **Bestellungen** schließen absichtlich Test- oder interne Bestellungen aus, die Google nicht unterscheiden kann.
* Unter bestimmten Umständen werden keine Bestellungen in Ihrer Datenbank aufgegeben.
* Google eCommerce-Tracking kennt keine Gutscheine und Rabatte für die Bestellung.
* Ihr Datenbank-Zeitstempel befindet sich in einer anderen Zeitzone als Ihr Google Analytics-Zeitstempel.

Denken Sie daran: Selbst wenn Google eine höhere Zahl als Ihre Datenbank meldet, fehlen ihr aus den im obigen Abschnitt beschriebenen Gründen wahrscheinlich noch einige Bestellungen.

## Fehlerbehebung

* Erstellen Sie einen Klon Ihrer **Umsatz**-Metrik ohne Filter, die das Ergebnis einschränken. Die Filter „Bestellungen, die wir zählen“ oder „Kunden, die wir zählen“ sind wichtig, aber Google hat keinen entsprechenden Filter.
* Überprüfen Sie einen kleinen aktuellen Zeitraum, z. B. einen Zeitraum von einigen Stunden vor dieser Woche.
* Nachdem Sie das E-Commerce-Tracking für Google in MBI eingerichtet haben, verwenden Sie Filter oder Gruppieren nach , um eine einzelne Source, Medium oder Kampagne zu prüfen. Führen Sie dann dasselbe in Google aus. Eine Quelle mit weniger Traffic/Umsatz ist besser, da sie wahrscheinlich weniger Fehlermarge hat.
