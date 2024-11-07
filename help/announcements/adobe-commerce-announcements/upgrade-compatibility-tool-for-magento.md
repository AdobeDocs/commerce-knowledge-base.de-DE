---
title: Upgrade-Kompatibilitätstool 1.1.0 für Adobe Commerce
description: Das Upgrade-Kompatibilitätstool 1.1.0 ist ein Befehlszeilen-Tool, das eine benutzerdefinierte Adobe Commerce-Instanz anhand einer bestimmten Version prüft, indem alle Module und der darin installierte Core-Code analysiert werden. Es wird eine Liste mit kritischen Fehlern, Problemen und Warnungen zurückgegeben, die behoben werden müssen, bevor auf die neueste Version von Adobe Commerce aktualisiert wird.
exl-id: 312abc5a-1d6a-4f32-9929-a94f4962eddd
feature: Upgrade
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---

# Upgrade-Kompatibilitätstool 1.1.0 für Adobe Commerce

Das Upgrade-Kompatibilitätstool 1.1.0 ist ein Befehlszeilen-Tool, das eine benutzerdefinierte Adobe Commerce-Instanz anhand einer bestimmten Version prüft, indem alle Module und der darin installierte Core-Code analysiert werden. Es wird eine Liste mit kritischen Fehlern, Problemen und Warnungen zurückgegeben, die behoben werden müssen, bevor auf die neueste Version von Adobe Commerce aktualisiert wird.

## Neue Funktionen bei UCT 1.1.0

Das Upgrade-Kompatibilitätstool 1.1.0 bietet bedeutende Verbesserungen, darunter:

* **Validieren Sie die Änderungen an den Kerndateien**: Adobe empfiehlt dringend, den Kern-Produktcode nicht anzupassen. Mit dieser Version haben wir einen Checkpoint für Kunden und Partner hinzugefügt, über den alle Änderungen am Kerncode identifiziert werden können, um die Auswirkungen der Änderungen frühzeitig und schnell zu verstehen. Durch das Hinzufügen dieses Tools innerhalb des Entwicklungsprozesses können Partner und Händler Probleme proaktiv identifizieren, Probleme bei zukünftigen Upgrades verhindern und die Gesamtbetriebskosten (Total Cost of Ownership, TCO) senken.
* **Exportieren des Berichts in eine JSON-Datei**: Diese Verbesserung wurde nach Feedback der Community implementiert. Wenn Sie das Tool jetzt ausführen, werden die Details aller identifizierten Probleme in eine JSON-Datei exportiert, damit Benutzer die Ergebnisse lesen, teilen und verwalten können, ohne das Tool erneut ausführen zu müssen.
* **Verbesserte VBE-Validierungen**: VBEs (Anbieter-Bundle-Erweiterungen) sind nicht Teil des Adobe Commerce-Core-Codes, werden jedoch von Adobe getestet und unterstützt. Mit dieser Aktualisierung validieren wir jetzt VBEs anhand des gleichen Ansatzes, den wir für Kerncode verwenden. Diese Verbesserung hilft Benutzern, Probleme im Zusammenhang mit Anpassungen und Kerncode/VBEs klar zu verstehen.
* **Bereitstellen von Fehlercodes**: Wir haben Fehlercodes eingeführt, mit denen Benutzer Probleme während eines Upgrades identifizieren, verstehen und lösen können. Fehler- und Warnmeldungen enthalten eine klare Beschreibung und eine empfohlene Lösung.
* **Möglichkeit, nur kritische Probleme aufzulisten**: Dadurch können sich Benutzer nur auf kritische Probleme konzentrieren und verursachen Probleme beim Aktualisieren.
* **Delta-Probleme zwischen zwei Versionen**: Mit dieser von unseren Community-Mitgliedern vorgeschlagenen Verbesserung können UCT-Benutzer eine Delta der Probleme zwischen zwei Versionen erhalten, wodurch sie sich nur auf die neuen Probleme konzentrieren können, die für die Zielversion eingeführt wurden, die sie aktualisieren werden.

## Welche Versionen kann das Tool vergleichen?

Sie können das Tool verwenden, um eine beliebige Version von 2.x zu vergleichen.

## Wer kann das Upgrade-Kompatibilitätstool 1.1.0 verwenden?

Adobe Commerce-Kunden.

## Installieren des Upgrade-Kompatibilitätstools 1.1.0

Installationsschritte finden Sie unter Adobe Commerce: [Upgrade-Kompatibilitätstool > Installieren](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/run) in unserer Entwicklerdokumentation. Voraussetzungen für die Verwendung des Tools finden Sie unter Adobe Commerce: [Upgrade-Kompatibilitätstool](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/prerequisites) in unserer Entwicklerdokumentation.

## Wie hoch ist die Zahl neben jedem Problem?

Dies ist die Fehlernachrichten-Referenz, die Informationen zu Fehlern enthält, die beim Ausführen des Upgrade-Kompatibilitätstools auftreten können.

Die Fehlermeldungen des Upgrade-Kompatibilitätstools sind nach Ebene (kritische Probleme, Fehler und Warnungen) und Typ (Kerncode, benutzerdefinierter Code und GraphQL-Schemata) kategorisiert. Jeder Typ enthält die folgenden Informationen:

* Fehlercode: Die Adobe Commerce-Kennung, die der Fehlermeldung zugewiesen ist.
* Fehlerbeschreibung: Eine Beschreibung, die die Fehlerursache zusammenfasst.
* Fehlerempfehlung: Falls zutreffend, enthält Anleitungen zur Fehlerbehebung und Fehlerbehebung.
* Codes werden auf der Referenzseite [Fehlermeldung](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/reporting/error-messages) aufgeführt und beschrieben.

## Wo kann ich Feedback zu dem Tool teilen?

Sie können sich an das UCT-Team in unserem Slack-Kanal [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F) wenden. Wir freuen uns auf Ihr Feedback und Ihre Vorschläge zur Verbesserung des Tools.

## Verwandte Informationen

* Adobe Commerce-Blog: [Einführung des Upgrade-Kompatibilitätstools (Alpha)](https://magento.com/blog/magento-news/introducing-upgrade-compatibility-tool)
* Adobe Commerce: [Upgrade-Kompatibilitätstool](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview) in unserer Entwicklerdokumentation.
