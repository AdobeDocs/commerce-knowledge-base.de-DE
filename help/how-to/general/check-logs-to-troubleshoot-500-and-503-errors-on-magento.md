---
title: Überprüfen Sie die Protokolle zur Fehlerbehebung bei 500- und 503-Fehlern in Adobe Commerce.
description: In diesem Artikel wird erläutert, wie Sie "access.log"und die zugehörigen Protokolle überprüfen können, um Fehler der Typen 503 und 500 zu beheben, die durch Datenverkehr oder unzureichende Serverressourcen verursacht werden können. Die Anzeige von "access.log"und zugehörigen Protokollen kann Informationen darüber liefern, welche Probleme im Zusammenhang mit Adobe Commerce in der Cloud-Infrastruktur auftreten können.
exl-id: 47d7de6b-3e12-4e79-a5c1-c27a9196b99c
feature: Cloud, Logs
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# Überprüfen Sie die Protokolle zur Fehlerbehebung bei 500- und 503-Fehlern in Adobe Commerce.

In diesem Artikel wird erläutert, wie Sie die `access.log` und die zugehörigen Protokolle überprüfen können, um Fehler der Typen 503 und 500 zu beheben, die durch Traffic oder unzureichende Serverressourcen verursacht werden können. Durch die Anzeige von &quot;`access.log`&quot;und den zugehörigen Protokollen können Informationen dazu bereitgestellt werden, welche Probleme im Zusammenhang mit Adobe Commerce in der Cloud-Infrastruktur verursachen können.

<!--
Bob - not in TOC
-->

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle [unterstützten Versionen](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html).

Um Protokolle für diese Serverfehler anzuzeigen, überprüfen Sie die `access.log` auf dem Webserver, z. B. `<ip address>` `<timestamp>` `<request uri>` `<response code>` `<referer url>`

So überprüfen Sie verwandte Protokolle:

1. Führen Sie den folgenden Befehl in der CLI aus, wenn er am aktuellen Tag ausgeführt wird (für die Adobe Commerce on Cloud Infrastructure Pro-Planarchitektur). Oder bis zu einem bestimmten Punkt in der Vergangenheit (für Adobe Commerce in der Starter-Planarchitektur der Cloud-Infrastruktur), da die Abdeckung der Protokolle begrenzt ist und keine Protokollrotation verfügbar ist: `grep -r "\" [50[0-9]" /path/to/access.log` Wenn der Fehler in der Vergangenheit aufgetreten ist, führen Sie den folgenden Befehl in der CLI aus (nur Pro-Architektur): `zgrep "\" 50[0-9]" /path/to/access.log.<rotation ID>.gz`
1. Überprüfen Sie dann die `exception.log` und `error.log` oder das entsprechende [gedrehte Protokoll](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html#log-rotation) (Protokolle, die automatisch gedreht und komprimiert werden, wenn sie eine bestimmte Dateigröße erreichen) für denselben Zeitstempel, um den potenziellen Fehler zu finden und zu sehen, was möglicherweise aufgetreten ist. Hinweis: Um die `exception.log` und `error.log` zu überprüfen, führen Sie die oben genannten Befehle in der CLI aus, ersetzen Sie jedoch `access.log` durch `exception.log` oder `error.log`.

## Verwandtes Lesen

* Siehe [Anzeigen und Verwalten von Protokollen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html) im *Adobe Commerce on Cloud Infrastructure Guide*.
* Siehe [Fehlerbehebung bei 503 Fehlern](/help/troubleshooting/miscellaneous/troubleshooting-503-errors.md) in unserer Support-Wissensdatenbank.
* Siehe [Magento Site-Down-Fehlerbehebung](/help/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.md) in unserer Support-Wissensdatenbank.
