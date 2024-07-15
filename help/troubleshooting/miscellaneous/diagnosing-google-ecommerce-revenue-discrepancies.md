---
title: Google-eCommerce-Umsatzdiskrepanzen diagnostizieren
description: '"Dieser Artikel bietet Lösungen für Diskrepanzen zwischen Google und Magento Business Intelligence (MBI). Das Google eCommerce-Tracking ermöglicht sowohl Ihr Google Analytics-Konto als auch Ihre MBI-Dashboards, aber es stellt viele Kunden in Frage: Sollten beide Tools die gleiche Anzahl von **Bestellungen** und **Umsatz** melden?'''
exl-id: b2e43e70-d234-4338-ae81-fa401416be5a
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 0%

---

# Google-eCommerce-Umsatzdiskrepanzen diagnostizieren

Dieser Artikel bietet Lösungen für Diskrepanzen zwischen Google und Magento Business Intelligence (MBI). Das eCommerce-Tracking von Google ermöglicht sowohl Ihr Google Analytics-Konto als auch Ihre MBI-Dashboards, aber es stellt sich heraus, dass viele Kunden uns fragen: Sollten beide Tools dieselbe Anzahl von **Bestellungen** und **Umsatz** melden?

Aus unserer Erfahrung heraus ist die Antwort in fast allen Fällen &quot;Nein&quot;. Das liegt daran, dass das Google eCommerce-Tracking die Bestellinformationen während eines Schaltflächen-Klickereignisses auf Ihrer Website erhält. Dadurch werden viele Bestellattribute, die später in Ihrer Datenbank gespeichert wurden, nicht berücksichtigt - von Bestellungen, die nicht registriert wurden, bis hin zu späteren Stornierungen oder Erstattungen.

Wir wissen, dass eine Diskrepanz zwischen Google und MBI Unsicherheit für Sie und Ihr Team hervorrufen kann. Wir möchten Ihnen dabei helfen, den Unterschied zwischen diesen beiden Zahlen zu verstehen, der Anpassungen für Ihr Google-Konto oder Ihre-Datenbank aufzeigen könnte.

## Warum meldet GA den Umsatz **weniger als** als meine Datenbank?

Wenn Google Analytics Bestellungen und Umsatz unterschätzen, ist dies ein Hinweis darauf, dass nicht alle Bestellungen auf Ihrer Site erfasst werden. Da Sie wissen, dass Ihre Datenbankdaten die eindeutige Nummer sind, können Sie einige Schritte unternehmen, um die Grundursache zu ermitteln - und möglicherweise dazu beitragen, dass Google weitere Informationen erfasst.

* Das Google eCommerce-Tracking war nicht immer aktiviert. Versuchen Sie, einen kleineren, aktuelleren Zeitraum zu betrachten.
* Ihr Google eCommerce-Tracking ist nicht so eingerichtet, dass es Käufe von bestimmten Browsern, Betriebssystemen oder Geräten erfasst.
* Das Klick-Ereignis, das mit Ihrem Google-E-Commerce-Tracking verknüpft ist, verfolgt Steuern, Sendungen oder andere Gebühren, die über der Bestellsumme liegen, nicht korrekt.
* Ihr Datenbankzeitstempel befindet sich in einer anderen Zeitzone als Ihr Google Analytics-Zeitstempel.
* Personen können Ihre Site über Inkognito-Fenster oder ausgeschaltete Cookies besuchen.

## Warum meldet GA den Umsatz **über dem Umsatz meiner Datenbank?**

Wir haben festgestellt, dass es für Google Analytics häufiger ist, Bestellungen und Umsätze im Vergleich zu einer E-Commerce-Datenbank zu überschreiben. Das ist nicht immer etwas Schlechtes. Ihre Datenbank ist der endgültige Datensatz zu Transaktionen, die auf Ihrer Website getätigt wurden. Es gibt mehrere Gründe, warum Google auch dann einen hohen Meldebestand hat, wenn Sie sie perfekt eingerichtet haben:

* Beim eCommerce-Tracking werden doppelte Schaltflächen-Klicks erfasst, die sich nur als eine einzige Bestellung in Ihrer Datenbank registrieren.
* Sie haben eine hohe Anzahl von stornierten, rückerstatteten oder betrügerischen Bestellungen. Dies ist eine Statusänderung, die nach der Nachverfolgung der Daten durch eCommerce stattfindet.
* Ihre Metriken **Umsatz** und **Bestellungen** schließen absichtlich Test- oder interne Bestellungen aus, die von Google nicht unterschieden werden können.
* Bestellungen können unter bestimmten Umständen nicht in Ihre Datenbank aufgenommen werden.
* Beim eCommerce-Tracking in Google sind keine Gutscheine und Rabatte für die Bestellung verfügbar.
* Ihr Datenbankzeitstempel befindet sich in einer anderen Zeitzone als Ihr Google Analytics-Zeitstempel.

Denken Sie daran, dass Google aus den im obigen Abschnitt beschriebenen Gründen wahrscheinlich immer noch einige Bestellungen vermisst, selbst wenn es eine höhere Anzahl als Ihre Datenbank meldet.

## Fehlerbehebung

* Erstellen Sie einen Klon Ihrer Metrik **Umsatz** ohne Filter, die das Ergebnis einschränken. Die Filter &quot;Bestellungen, die wir zählen&quot;oder &quot;Kunden, denen wir zählen&quot;sind wichtig, Google hat jedoch keinen entsprechenden Filter.
* Prüfen Sie einen kleinen letzten Zeitraum, z. B. eine Zeitspanne von einigen Stunden Anfang dieser Woche.
* Nachdem Sie das Google eCommerce-Tracking in MBI eingerichtet haben, verwenden Sie Filter oder Group-By , um eine einzelne Source, Medium oder Campaign zu prüfen. Gehen Sie dann in Google genauso vor. Eine Quelle mit weniger Traffic/Umsatz ist besser, da sie wie eine weniger Fehlermarge aufweist.
