---
title: Häufig gestellte Fragen zur aktualisierten Lebenszyklusrichtlinie für Adobe Commerce-Versionen
description: "Adobe Commerce bietet Qualitätsverbesserungen für eine Nebenversion für mindestens 12 Monate ab dem allgemeinen Verfügbarkeitsdatum der nächsten kleineren Softwareversion. Die Art und Weise, wie wir während dieses Zeitraums Qualitätsverbesserungen vornehmen, ändert sich:"
exl-id: 4aa601d0-ee1d-4f1f-a684-188772a58dd1
feature: Compliance, Support
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '1176'
ht-degree: 0%

---

# Häufig gestellte Fragen zur aktualisierten Lebenszyklusrichtlinie für Adobe Commerce-Versionen

## Was ändert sich?

Adobe Commerce bietet Qualitätsverbesserungen für eine Nebenversion von mindestens 12 Monaten ab dem allgemeinen Verfügbarkeitsdatum der nächsten kleineren Softwareversion. Die Art und Weise, wie wir während dieses Zeitraums Qualitätsverbesserungen bereitstellen, ändert sich:

* **Vorherige Richtlinie:** Derzeit werden die Qualitätsverbesserungen für die vorherige Zeile, die sich im 12-monatigen EOS-Fenster befindet, über unsere vierteljährliche Patch-Version bereitgestellt. Dadurch werden die vierteljährlichen Patches zu einer Kombination aus Sicherheit und Qualität.
* **Neue Richtlinie:** Ab Version 2.4 als aktuellster Nebenversion werden Release-Patches für die vorherige unterstützte Zeile (2.3) nur für die Sicherheit angezeigt. Wir stellen weiterhin Qualitätsverbesserungen für die vorherige unterstützte Zeile während des 12-Monats-Fensters nach der Veröffentlichung einer kleineren Version (z. B. 2.4) und nachfolgender neuer Nebenversionen bereit. Diese werden jedoch über das [Qualitäts-Patches-Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) bereitgestellt und nur auf kritische Probleme ausgerichtet.

## Wann tritt diese Politik in Kraft?

Adobe Commerce 2.3.6 wird voraussichtlich am 15. Oktober 2020 veröffentlicht. Es ist als letzte Patch-Version für Adobe Commerce 2.3 geplant, die sowohl Qualität als auch Sicherheit umfasst. Nach 2.3.6 wird die 2.3.x-Zeile sicher sein, und kritische Qualitätsprobleme für 2.3 können über QPT behoben werden.

>[!NOTE]
>
>Das einzige Mal, dass wir eine Vollversion von 2.3 veröffentlichen, ist, wenn wir die Einhaltung unserer Technologie-Stack, wie z.B. für PHP oder Elasticsearch, beibehalten müssen. Dies geschieht in Q2 von 2021 mit einem obligatorischen Update von PHP 7.4, wir werden die Zeile auf 2.3.7 erhöhen. Weitere Informationen finden Sie in der [PHP 7.4-Unterstützung für Adobe Commerce 2.3.x-Release-Zeile](https://community.magento.com/t5/Magento-DevBlog/PHP-7-4-support-for-Magento-2-3-x-release-line/ba-p/458946) DevBlog-Beitrag.

## Was ist eine Nur-Sicherheit-Version?

Nur-Sicherheitsversionen enthalten nur Sicherheitskorrekturen und keine behobene Qualität. Beachten Sie jedoch, dass unsere reinen Sicherheitsversionen spezifische Hotfixes enthalten können, wenn wir diese für die Ausführung von Adobe Commerce für absolut wichtig halten.

## Wird es weiterhin eine Nur-Sicherheit-Version für die neueste Zeile (ab Veröffentlichung 2.4) geben?

Adobe wird auch für die neueste Release-Zeile weiterhin nur sicherheitsrelevante Versionen haben. Der Prozess dafür wird in [Einführung der neuen reinen Sicherheits-Patch-Version](https://community.magento.com/t5/Magento-DevBlog/Introducing-the-New-Security-only-Patch-Release/ba-p/141287) DevBlog-Beitrag beschrieben.

## Was ist das Werkzeug für Qualitätsmuster?

Lesen Sie diesbezüglich auch den Artikel [Qualitätspatches-Tool: Ein neues Tool zur Selbstbedienung von Qualitäts-Patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in unserer Support-Wissensdatenbank.

## Wer sollte die Verwendung dieser neuen Richtlinie in Erwägung ziehen?

Die neue Politik soll den Händlern die Möglichkeit geben, strategisch für die jährlichen Entwicklungskosten der Adobe Commerce zu planen, während sie gleichzeitig die Sicherheit und kritische Qualität während dieser strategischen Zyklen wahren können. Es kann auch von Händlern genutzt werden, die sich um Sicherheit über alles andere kümmern und im Allgemeinen mit der Stabilität älterer unterstützter Linien zufrieden sind. Für Händler ist es möglicherweise einfacher, diese Upgrades zu planen und zu finanzieren, da sie berechenbarer sind.

## Sollten Merchants weiterhin auf die neueste Version aktualisieren?

Letztlich sollten alle Merchants-Unternehmen der Planung weiterhin Priorität einräumen, um die neueste Adobe Commerce-Linie rechtzeitig zu übernehmen. Die neue Sicherheitslinie und das QPT-Tool sollen nicht die strategische Upgrade-Roadmap für Händler ersetzen, sondern den Händlern Flexibilität bei der Planung ihrer Upgrade-Roadmap bieten und eine Möglichkeit bieten, schnell auf Sicherheits-/Qualitätsprobleme zu reagieren, ohne eine komplette Aktualisierung durchführen zu müssen.

## Wie erhalte ich Qualitätsverbesserungen für unterstützte Nebenversionen, die nicht die neueste Zeile sind?

Korrekturen werden über das [Qualitätspatches-Tool](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) bereitgestellt.

## Wie erhalte ich Qualitätsverbesserungen in der neuesten Zeile?

Die aktuelle Zeile wird im Rahmen der vierteljährlichen Aktualisierung von hoher Qualität sein. Wenn Sie sich zwischen den Versionen für eine Fehlerbehebung in der neuesten Zeile an den Support wenden, wird dieser über QPT bereitgestellt. Wenn Sie dann ein Upgrade auf die Version durchführen, in der diese Korrektur enthalten ist, wird sie über den vierteljährlichen Patch angewendet.

## Welche Qualitätsprobleme werden bei unterstützten Nebenversionen behoben, die nicht die neueste Zeile sind?

Nur wichtige Qualitätsprobleme, die die Kernflüsse unterbrechen, werden in der vorherigen Zeile (2.3) behoben und über QPT bereitgestellt.

## Sind Qualitätskorrekturen Teil der vierteljährlichen Version bei unterstützten kleineren Versionen, die nicht die neueste Version sind?

Ja, im Rahmen der Sicherheitslinie veröffentlichen wir das, was Adobe &quot;Hotfixes&quot;nennt, an diese Zeile. Dies sind äußerst kritische Probleme, die sich auf die Adobe Commerce-Anwendung auswirken.

## Werden Sicherheitsverbesserungen und QPT gleichzeitig bereitgestellt?

Die Zeile &quot;Nur Sicherheit&quot;entspricht dem vierteljährlichen Veröffentlichungszeitplan und wird mit der Nomenklatur -p1 veröffentlicht. Beispiel 2.3.6-p1. Qualität wird ad hoc veröffentlicht, wenn Qualitätsprobleme erkannt und behoben werden und sie über QPT verfügbar gemacht werden.

## Was mache ich, wenn ich ein Qualitätsproblem habe, das in unterstützten Nebenversionen, die nicht die neueste Zeile oder QPT sind, nicht behoben wird?

Die vorherige Zeile ist nur Sicherheit, was bedeutet, dass der Hauptvorteil sicher bleibt. Mit QPT werden nur Patches für wichtige Probleme bereitgestellt, die die Kernflüsse unterbrechen.

Probleme, die sich nicht auf die Kernflüsse auswirken oder Problemumgehungen aufweisen, werden nur in der neuesten Zeile behoben. Adobe ermutigt diejenigen, die sowohl kritische als auch nicht kritische Korrekturen wünschen, zur neuesten Zeile zu wechseln.

## Werden Upgrades für Merchants teurer oder schwieriger, wenn sie auf der Sicherheitslinie bleiben, bis sie das Ende der Sicherheitsunterstützung erreichen?

Theoretisch sollten sie die Kosten für den Merchant in Bezug auf Entwicklungszeiten gleich hoch sein, solange sie nicht eine große Anzahl von Qualitätspatches eingeführt haben. Wenn ein Händler feststellt, dass er mehr als eine Handvoll Patches über das QPT-Tool benötigt oder möchte, wird empfohlen, ein Upgrade auf die neueste Version von Adobe Commerce zu priorisieren. Durch die Übernahme einer großen Anzahl von Qualitätspatches anstelle der Aktualisierung auf die aktuelle Version von Adobe Commerce können die Entwicklungskosten und die Komplexität der Aktualisierung erhöht werden, sobald die Nur-Sicherheit-Verbindung das Ende der Unterstützung erreicht.

## Warum sollte ich die Anzahl der über QPT bereitgestellten Qualitäts-Patches begrenzen?

Durch die Anwendung vieler individueller Qualitätsverbesserungen wird der Adobe Commerce-Code komplexer. Die zusätzliche Komplexität kann zu unvorhersehbaren Änderungen führen, wenn ein Upgrade auf die neueste Release-Zeile durchgeführt wird. Deshalb empfehlen wir, QPT sparsam und nur für die kritischsten Korrekturen zu verwenden.

## Wie sieht es mit der Einhaltung von Technologiestapeln aus?

Während der Lebensdauer einer Release-Zeile wird es Updates zu verschiedenen Technologie-Stacks wie PHP oder Elasticsearch geben, die aktualisiert werden müssen, um kompatibel zu bleiben. Wir werden unseren Händlern so gut wie möglich darauf aufmerksam machen, dass diese kommen.

Hinweis: Im 2. Quartal 2021 müssen wir PHP und Redis auf der 2.3.x-Zeile aktualisieren, um weiterhin kompatibel zu sein. Dadurch wird die Zeile auf 2.3.7 erhöht. Weitere Informationen finden Sie in der [PHP 7.4-Unterstützung für Adobe Commerce 2.3.x-Release-Zeile](https://community.magento.com/t5/Magento-DevBlog/PHP-7-4-support-for-Magento-2-3-x-release-line/ba-p/458946) DevBlog-Beitrag.
