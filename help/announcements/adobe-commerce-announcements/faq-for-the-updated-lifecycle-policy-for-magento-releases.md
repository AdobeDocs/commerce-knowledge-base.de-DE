---
title: Häufig gestellte Fragen zur aktualisierten Lebenszyklusrichtlinie für Adobe Commerce-Versionen
description: 'Adobe Commerce bietet Qualitätskorrekturen für eine Nebenversion für mindestens 12 Monate ab dem allgemeinen Verfügbarkeitsdatum der nächsten Nebenversion der Software. Die Art und Weise, wie wir in diesem Zeitraum Qualitätskorrekturen bereitstellen, ändert sich:'
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

Adobe Commerce bietet Qualitätskorrekturen für eine Nebenversion für mindestens 12 Monate ab dem allgemeinen Verfügbarkeitsdatum der nächsten Nebenversion der Software. Die Art und Weise, wie wir in diesem Zeitraum Qualitätskorrekturen bereitstellen, ändert sich:

* **Vorherige Richtlinie:** Derzeit werden die Qualitätskorrekturen für die vorherige Zeile, die im 12-monatigen EOS-Fenster enthalten ist, über unsere vierteljährliche Patch-Version bereitgestellt. Dadurch stellen die vierteljährlichen Patches eine Kombination aus Sicherheit und Qualität dar.
* **Neue Richtlinie:** Ab 2.4 als aktuellste Nebenversion werden die Veröffentlichungs-Patches für die vorherige unterstützte Zeile (2.3) auf „Nur Sicherheit“ umgestellt. Wir werden auch während des 12-monatigen Zeitfensters nach der Veröffentlichung einer Nebenversion (wie 2.4) und nachfolgender neuer Nebenversionen Qualitätskorrekturen für die vorherige unterstützte Zeile bereitstellen. Diese werden jedoch über das [Quality Patches Tool (QPT) verfügbar gemacht ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) sich nur auf kritische Probleme konzentrieren.

## Wann tritt diese Richtlinie in Kraft?

Adobe Commerce 2.3.6 wird voraussichtlich am 15. Oktober 2020 veröffentlicht und ist die letzte Patch-Version für Adobe Commerce 2.3, die sowohl Qualität als auch Sicherheit umfasst. Nach 2.3.6 wird die 2.3.x-Zeile nur noch für Sicherheitsfragen relevant und kritische Qualitätsprobleme für 2.3 können per QPT behoben werden.

>[!NOTE]
>
>Die einzige Zeit, in der wir eine Vollversion von 2.3 veröffentlichen, ist, wenn wir die Einhaltung unseres Technologie-Stacks, wie z. B. für PHP oder Elasticsearch, beibehalten müssen. Dies geschieht im 2. Quartal 2021 mit einem obligatorischen Update von PHP 7.4, wir werden die Zeile auf 2.3.7 erhöhen. Weitere Informationen finden Sie unter [PHP 7.4-Unterstützung für Adobe Commerce 2.3.x-Release](https://community.magento.com/t5/Magento-DevBlog/PHP-7-4-support-for-Magento-2-3-x-release-line/ba-p/458946) DevBlog-Beitrag.

## Was ist eine reine Sicherheitsversion?

Nur-Sicherheits-Versionen enthalten nur Sicherheitskorrekturen und keine Qualitätskorrekturen. Beachten Sie jedoch, dass unsere Nur-Sicherheit-Versionen möglicherweise spezifische Hotfixes enthalten, wenn wir diese für die Ausführung von Adobe Commerce als absolut wichtig erachten.

## Wird es für die neueste Zeile (ab Veröffentlichung 2.4) weiterhin eine reine Sicherheitsversion geben?

Adobe wird auch weiterhin nur sicherheitsrelevante Versionen für die neueste Release-Zeile haben. Der Prozess dafür wird im DevBlog-Beitrag [Einführung in die neue, reine Sicherheits](https://community.magento.com/t5/Magento-DevBlog/Introducing-the-New-Security-only-Patch-Release/ba-p/141287)Patch-Version beschrieben.

## Was ist das Quality Patches Tool?

Weitere Informationen finden Sie im [Quality Patches Tool Release: a new tool to self-serve quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) Artikel in unserer Support Knowledge Base.

## Wer sollte in Betracht ziehen, diese neue Richtlinie anzuwenden?

Mit der neuen Richtlinie sollen Wege geschaffen werden, damit Händler die jährlichen Entwicklungskosten für Adobe Commerce strategisch planen können, während sie gleichzeitig die Sicherheit und kritische Qualität während dieser strategischen Zyklen aufrechterhalten können. Es kann auch von Händlern genutzt werden, die sich um die Sicherheit über alles andere kümmern und im Allgemeinen mit der Stabilität älterer, unterstützter Linien zufrieden sind. Händler finden es möglicherweise einfacher, diese Upgrades zu planen und zu budgetieren, da sie vorhersehbarer sind.

## Sollten Händler weiterhin auf die neueste Produktlinie aktualisieren?

Letztlich sollten alle Händler weiterhin die Planung zur zeitnahen Einführung der neuesten Adobe Commerce-Produktlinie priorisieren. Die neue Security Only-Linie und das QPT-Tool sollen die strategische Upgrade-Roadmap für Händler nicht ersetzen, sondern bieten Händlern Flexibilität bei der Planung ihrer Upgrade-Roadmap und eine Möglichkeit, schnell auf Sicherheits-/Qualitätsprobleme zu reagieren, ohne ein komplettes Upgrade implementieren zu müssen.

## Wie erhalte ich Qualitätskorrekturen für unterstützte Nebenversionen, bei denen es sich nicht um die neueste Zeile handelt?

Fehlerbehebungen werden über das [Quality Patches Tool) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).

## Wie erhalte ich Qualitätskorrekturen für die neueste Zeile?

Die aktuelle Zeile wird im Rahmen der vierteljährlichen Aktualisierung qualitativ hochwertig sein. Wenn Sie zwischen den Versionen den Support kontaktieren, um eine Fehlerbehebung für die neueste Zeile zu erhalten, wird diese über QPT bereitgestellt. Wenn Sie dann auf die Version aktualisieren, in der diese Fehlerbehebung enthalten ist, wird sie über den vierteljährlichen Patch angewendet.

## Welche Qualitätsprobleme werden in unterstützten Nebenversionen behoben, die nicht die neueste Zeile sind?

Nur wichtige Qualitätsprobleme, die den Kernfluss unterbrechen, werden in der vorherigen Zeile (2.3) behoben und über QPT bereitgestellt.

## Sind alle Qualitätskorrekturen Teil der vierteljährlichen -Version für unterstützte Nebenversionen, die nicht die neueste Zeile sind?

Ja, als Teil der reinen Sicherheitslinie veröffentlichen wir, was Adobe als „Hotfixes“ bezeichnet, in dieser Zeile. Dies sind äußerst wichtige Probleme, die sich auf die Adobe Commerce-Anwendung auswirken.

## Werden gleichzeitig Sicherheitsverbesserungen und QPT bereitgestellt?

Die Zeile „Nur Sicherheit“ folgt dem vierteljährlichen Veröffentlichungszeitplan und wird mit der -p1-Nomenklatur veröffentlicht. Beispiel 2.3.6-p1. Die Qualität wird ad hoc veröffentlicht, wenn Qualitätsprobleme erkannt und behoben werden, und sie werden über QPT zur Verfügung gestellt.

## Was kann ich tun, wenn ich ein Qualitätsproblem habe, das nicht in unterstützten Nebenversionen behoben wird, die nicht die neueste Zeile oder das neueste QPT sind?

Da die vorherige Zeile nur für Sicherheit ausgelegt ist, ist der Hauptvorteil die Sicherheit. Nur Patches für wichtige Probleme, die den Kernfluss unterbrechen, werden über QPT zur Verfügung gestellt.

Probleme, die sich nicht auf Kernflüsse auswirken oder die Problemumgehungen aufweisen, werden nur in der letzten Zeile behoben. Adobe empfiehlt allen Benutzern, die sowohl kritische als auch nicht kritische Fehlerbehebungen wünschen, zur aktuellen Zeile zu wechseln.

## Werden Upgrades für Händler teurer oder schwieriger, wenn sie bis zum Ende des Sicherheits-Supports auf der Nur-Sicherheits-Linie bleiben?

Theoretisch sollten die Kosten für den Händler in Bezug auf die Entwicklungsstunden gleich sein, solange er nicht eine große Anzahl von Qualitätspatches angenommen hat. Wenn ein Händler über das QPT-Tool feststellt, dass er mehr als eine Handvoll Patches benötigt oder möchte, wird empfohlen, ein Upgrade auf die neueste Version von Adobe Commerce zu priorisieren. Wenn Sie nicht auf die aktuelle Version von Adobe Commerce aktualisieren, sondern eine große Anzahl von Qualitäts-Patches einsetzen, können die Entwicklungskosten und die Komplexität von Upgrades steigen, sobald die Nur-Sicherheit-Produktlinie das Ende der Unterstützung erreicht hat.

## Warum sollte ich die Anzahl der Qualitäts-Patches begrenzen, die über QPT bereitgestellt werden?

Durch die Anwendung vieler individueller Qualitätskorrekturen wird Ihr Adobe Commerce-Code komplexer. Die zusätzliche Komplexität kann beim Upgrade auf die neueste Version zu unvorhersehbaren Änderungen führen. Deshalb empfehlen wir, QPT sparsam und nur für die wichtigsten Fehlerbehebungen zu verwenden.

## Wie sieht es mit der Compliance für Technologie-Stacks aus?

Während der Lebensdauer einer Release-Line wird es Updates für verschiedene Technologie-Stacks wie PHP oder Elasticsearch geben, die aktualisiert werden müssen, um konform zu bleiben. Wir werden unseren Händlern so viel wie möglich mitteilen, dass diese kommen.

Hinweis: Im 2. Quartal 2021 müssen wir PHP und Redis auf der 2.3.x-Zeile aktualisieren, um konform zu bleiben. Dadurch wird die Zeile auf 2.3.7 erhöht. Weitere Informationen finden Sie unter [PHP 7.4-Unterstützung für Adobe Commerce 2.3.x-Release](https://community.magento.com/t5/Magento-DevBlog/PHP-7-4-support-for-Magento-2-3-x-release-line/ba-p/458946) DevBlog-Beitrag.
