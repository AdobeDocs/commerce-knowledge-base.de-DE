---
title: 'SQL-Abfragen: Fehler bei Kosten erläutern'
description: Dieser Artikel enthält Lösungen für Fehler bei EXPLAIN-Kosten bei der Ausführung nicht erfolgreicher SQL-Abfragen. PostgreSQL verwendet etwas namens [EXPLAIN-Befehl](https://www.postgresql.org/docs/9.5/static/using-explain.html), um die Kosten von SQL-Abfragen zu ermitteln. Wir haben den SQL-Report Builder erstellt, um diesen Befehl ebenfalls zu verwenden. Das bedeutet, dass die Abfrage nicht ausgeführt wird und eine EXPLAIN-Meldung angezeigt wird, wenn die Kosten als zu hoch gelten - die für die Ausführung der Abfrage erforderliche Ressourcenmenge überschreitet die Schwellenwerte.
exl-id: 6f6df66a-665e-46a8-ad4c-842a0270c4eb
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# SQL-Abfragen: Fehler bei EXPLAIN-Kosten

Dieser Artikel enthält Lösungen für Fehler bei EXPLAIN-Kosten bei der Ausführung nicht erfolgreicher SQL-Abfragen. PostgreSQL verwendet etwas namens [EXPLAIN-Befehl](https://www.postgresql.org/docs/9.5/static/using-explain.html), um die Kosten von SQL-Abfragen zu ermitteln. Wir haben den SQL-Report Builder erstellt, um diesen Befehl ebenfalls zu verwenden. Das bedeutet, dass die Abfrage nicht ausgeführt wird und eine EXPLAIN-Meldung angezeigt wird, wenn die Kosten als zu hoch gelten - die für die Ausführung der Abfrage erforderliche Ressourcenmenge überschreitet die Schwellenwerte.

Es gibt einige Gründe, warum das passieren könnte. Hier finden Sie die Nachrichten, die Sie erhalten können, was sie bedeuten und wie Sie sie beheben können.

## Abfrage kann nicht ausgeführt werden. Der &quot;EXPLAIN&quot;-Kostenwert von \[xxx\] ist zu hoch, um diese Abfrage ausführen zu können.

Wenn diese Meldung angezeigt wird, bedeutet dies, dass die Ausführung der Abfrage als zu teuer erachtet wurde. Wir haben zwei Empfehlungen für diese Situation: eine besteht darin, alle ORDER BY-Klauseln aus Ihrer Abfrage zu streichen, da es sich um kostspielige Vorgänge handelt. Die zweite besteht darin, die Tipps in unserem [Optimierungsartikel](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/optimizing-your-sql-queries.html) zu befolgen, um Ihre Abfrage anzupassen.

## Abfrage kann nicht ausgeführt werden. Diese Abfrage gibt \[xxx\] Zeilen zurück, die unseren Grenzwert von 10.000 überschreiten.

In diesem Fall überschreitet die mögliche Anzahl von Ergebnissen die für den SQL-Report Builder festgelegte Höchstzahl. Es gibt verschiedene Möglichkeiten, die Anzahl der Ergebnisse zu reduzieren:

* Versuchen Sie, Ihrer Abfrage einige Filter hinzuzufügen.
* Verwenden Sie LIMIT, wenn Sie können. Einige Tabellen haben eine große Anzahl von Zeilen. Durch die Beschränkung der Ergebnisse bleiben Sie möglicherweise unter der Zeilenbegrenzung.

## EXPLAIN-Antwort kann nicht analysiert werden.

Oh, Diese Nachricht bedeutet normalerweise, dass auf unserer Seite wahrscheinlich etwas schiefgelaufen ist. Wenn Sie diesen Fehler weiterhin erhalten, wenden Sie sich an den Support.
