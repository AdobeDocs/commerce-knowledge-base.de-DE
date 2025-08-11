---
title: Überprüfen Sie die Protokolle, um Fehler vom Typ 500 und 503 in Adobe Commerce zu beheben.
description: In diesem Artikel wird erläutert, wie Sie „access.log“ und die zugehörigen Protokolle überprüfen können, um 503- und 500-Fehler zu beheben, die durch Traffic oder unzureichende Server-Ressourcen verursacht werden können. Die Anzeige von „access.log“ und zugehörigen Protokollen kann Informationen darüber liefern, was möglicherweise Probleme verursacht, die mit Adobe Commerce in der Cloud-Infrastruktur zusammenhängen.
exl-id: 47d7de6b-3e12-4e79-a5c1-c27a9196b99c
feature: Cloud, Logs
source-git-commit: 66ac9de94e9a4a1eccdb5aac1875ecf0a0637e90
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# Überprüfen Sie die Protokolle, um Fehler vom Typ 500 und 503 in Adobe Commerce zu beheben.

In diesem Artikel wird erläutert, wie Sie die `access.log` und zugehörigen Protokolle überprüfen können, um Fehler vom Typ 503 und 500 zu beheben, die durch Traffic oder unzureichende Serverressourcen verursacht werden können. Die Anzeige der `access.log` und der zugehörigen Protokolle kann Informationen zu den Ursachen von Problemen bereitstellen, die im Zusammenhang mit Adobe Commerce in der Cloud-Infrastruktur stehen.

<!--
Bob - not in TOC
-->

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, alle [unterstützten Versionen](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html?lang=de).

Um Protokolle auf diese Server-Fehler anzuzeigen, überprüfen Sie die `access.log` auf dem Webserver, z. B. `<ip address>` `<timestamp>` `<request uri>` `<response code>` `<referer url>`

So überprüfen Sie die zugehörigen Protokolle:

1. Führen Sie den folgenden Befehl in der CLI aus, sofern er am aktuellen Tag erfolgt (für Adobe Commerce auf Cloud Infrastructure Pro Planarchitektur). Oder zu einem bestimmten Zeitpunkt in der Vergangenheit (für die Starterplanarchitektur von Adobe Commerce in der Cloud-Infrastruktur), da die Dauer der Protokollabdeckung begrenzt ist und die Protokollrotation nicht verfügbar ist: `grep -r "\" [50[0-9]" /path/to/access.log` Wenn der Fehler in der Vergangenheit aufgetreten ist, führen Sie den folgenden Befehl in der CLI aus (nur Pro-Architektur): `zgrep "\" 50[0-9]" /path/to/access.log.<rotation ID>.gz`
1. Überprüfen Sie dann die `exception.log` und `error.log` oder das entsprechende [rotierte Protokoll](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html?lang=de#log-rotation) (Protokolle, die automatisch rotiert und komprimiert werden, wenn sie eine bestimmte Dateigröße erreichen) für denselben Zeitstempel, um den potenziellen Fehler zu finden und zu sehen, was möglicherweise passiert ist, das ihn verursacht hat. Hinweis: Um die `exception.log` zu überprüfen und `error.log` die oben genannten Befehle in der CLI ausführen, aber `access.log` durch `exception.log` oder `error.log` ersetzen.

## Verwandtes Lesen

* Siehe [Anzeigen und Verwalten von Protokollen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=de) im Handbuch zu *Adobe Commerce in Cloud-Infrastrukturen*.
* Siehe [Fehlerbehebung für 503-Fehler](/help/troubleshooting/miscellaneous/troubleshooting-503-errors.md) in unserer Support-Wissensdatenbank.