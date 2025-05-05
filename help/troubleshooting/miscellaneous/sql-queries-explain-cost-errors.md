---
title: 'SQL-Abfragen: Fehler bei EXPLAIN COST'
description: Dieser Artikel bietet Lösungen für ERKLÄRUNGSKOSTENFEHLER beim Ausführen nicht erfolgreicher SQL-Abfragen. PostgreSQL verwendet einen [EXPLAIN-Befehl](https://www.postgresql.org/docs/9.5/static/using-explain.html), um die Kosten von SQL-Abfragen zu ermitteln. Wir haben den SQL-Report Builder so erstellt, dass auch dieser Befehl verwendet wird. Das bedeutet, dass die Abfrage nicht ausgeführt wird und eine ERKLÄRUNGSMELDUNG angezeigt wird, wenn die Kosten als zu hoch erachtet werden - die für die Ausführung der Abfrage erforderliche Ressourcenmenge überschreitet unsere Schwellenwerte.
exl-id: 6f6df66a-665e-46a8-ad4c-842a0270c4eb
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# SQL-Abfragen: Fehler bei EXPLAIN COST

Dieser Artikel bietet Lösungen für ERKLÄRUNGSKOSTENFEHLER beim Ausführen nicht erfolgreicher SQL-Abfragen. PostgreSQL verwendet einen so genannten [EXPLAIN-Befehl](https://www.postgresql.org/docs/9.5/static/using-explain.html), um die Kosten von SQL-Abfragen zu ermitteln. Wir haben den SQL-Report Builder so erstellt, dass auch dieser Befehl verwendet wird. Das bedeutet, dass die Abfrage nicht ausgeführt wird und eine ERKLÄRUNGSMELDUNG angezeigt wird, wenn die Kosten als zu hoch erachtet werden - die für die Ausführung der Abfrage erforderliche Ressourcenmenge überschreitet unsere Schwellenwerte.

Es gibt einige Gründe, warum dies passieren könnte. Im Folgenden finden Sie Informationen über mögliche Probleme, ihre Bedeutung und Möglichkeiten zur Fehlerbehebung.

## Abfrage kann nicht ausgeführt werden. Der Wert von \[xxx\] für die ERKLÄRUNGSKOSTEN ist zu hoch, um diese Abfrage auszuführen.

Wenn Sie diese Meldung sehen, bedeutet dies, dass die Ausführung der Abfrage als zu teuer erachtet wurde. Für diese Situation haben wir zwei Empfehlungen: Erstens, alle ORDER BY-Klauseln aus Ihrer Abfrage zu entfernen, da es sich um kostspielige Operationen handelt. Die zweite Möglichkeit besteht darin, den Tipps in unserem [Optimierungsartikel](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/optimizing-your-sql-queries.html?lang=de) zu folgen, um Ihre Abfrage anzupassen.

## Abfrage kann nicht ausgeführt werden. Diese Abfrage gibt \[xxx\] Zeilen zurück, was unseren Grenzwert von 10.000 überschreitet

In diesem Fall überschreitet die mögliche Anzahl von Ergebnissen das für den SQL-Report Builder festgelegte Maximum. Es gibt einige Möglichkeiten, die Anzahl der Ergebnisse zu reduzieren:

* Versuchen Sie, Ihrer Abfrage einige Filter hinzuzufügen.
* Verwenden Sie LIMIT, falls möglich. Einige Tabellen enthalten eine große Anzahl von Zeilen, und durch die Begrenzung der Ergebnisse können Sie unter der Zeilenbegrenzung bleiben.

## Antwort von EXPLAIN kann nicht analysiert werden.

Hoppla. Diese Meldung bedeutet normalerweise, dass bei uns wahrscheinlich etwas schiefgelaufen ist. Wenn Sie diesen Fehler weiterhin erhalten, wenden Sie sich bitte an den Support.
