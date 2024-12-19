---
title: Upgrade-Kompatibilitäts-Tool 1.1.0 für Adobe Commerce
description: Das Upgrade-Kompatibilitäts-Tool 1.1.0 ist ein Befehlszeilen-Tool, das eine benutzerdefinierte Adobe Commerce-Instanz mit einer bestimmten Version vergleicht, indem es alle darin installierten Module und den Kern-Code analysiert. Sie gibt eine Liste mit kritischen Fehlern, Problemen und Warnungen zurück, die vor dem Upgrade auf die neueste Version von Adobe Commerce behoben werden müssen.
exl-id: 312abc5a-1d6a-4f32-9929-a94f4962eddd
feature: Upgrade
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---

# Upgrade-Kompatibilitäts-Tool 1.1.0 für Adobe Commerce

Das Upgrade-Kompatibilitäts-Tool 1.1.0 ist ein Befehlszeilen-Tool, das eine benutzerdefinierte Adobe Commerce-Instanz mit einer bestimmten Version vergleicht, indem es alle darin installierten Module und den Kern-Code analysiert. Sie gibt eine Liste mit kritischen Fehlern, Problemen und Warnungen zurück, die vor dem Upgrade auf die neueste Version von Adobe Commerce behoben werden müssen.

## Neue Funktionen in UCT 1.1.0

Das Upgrade-Kompatibilitäts-Tool 1.1.0 führt zu wichtigen Verbesserungen, einschließlich:

* **Validieren von Änderungen an Kerndateien**: Adobe empfiehlt dringend, den Code des Kernprodukts nicht anzupassen. Mit dieser Version haben wir einen Checkpoint für Kunden und Partner hinzugefügt, um Änderungen am Kern-Code zu identifizieren, damit die Auswirkungen der Änderungen frühzeitig und schnell erkannt werden können. Das Hinzufügen dieses Tools zum Entwicklungsprozess hilft Partnern und Händlern, Probleme proaktiv zu identifizieren, Probleme bei zukünftigen Upgrades zu vermeiden und die Total Cost of Ownership (TCO) zu senken.
* **Exportieren des Berichts in eine JSON-**: Diese Verbesserung wurde nach Feedback der Community implementiert. Wenn Sie das Tool jetzt ausführen, werden die Details aller identifizierten Probleme in eine JSON-Datei exportiert, sodass Benutzende die Ergebnisse lesen, freigeben und verwalten können, ohne das Tool erneut ausführen zu müssen.
* **Verbesserte VBE-**: VBEs (Vendor Bundled Extensions) sind nicht Teil des Adobe Commerce-Code, werden jedoch von Adobe getestet und unterstützt. Mit diesem Update validieren wir VBEs nun mit demselben Ansatz, den wir für den Kern-Code verwenden. Diese Verbesserung hilft Benutzenden, Probleme im Zusammenhang mit Anpassungen und Core-Code/VBEs klar zu verstehen.
* **Angabe von Fehlercodes**: Wir haben Fehlercodes eingeführt, die Benutzern dabei helfen, Probleme während eines Upgrades zu identifizieren, zu verstehen und zu lösen. Fehler- und Warnmeldungen bieten eine klare Beschreibung und Lösungsvorschläge.
* **Möglichkeit, nur kritische Probleme aufzulisten**: Auf diese Weise können sich Benutzer nur auf die kritischen Probleme konzentrieren, die beim Upgrade Probleme verursachen.
* **Delta-Probleme zwischen zwei Versionen**: Mit dieser von unseren Community-Mitgliedern vorgeschlagenen Verbesserung können UCT-Benutzer ein Delta der Probleme zwischen zwei Versionen erhalten, sodass sie sich nur auf die neuen Probleme konzentrieren können, die für die Zielversion eingeführt wurden, die sie aktualisieren werden.

## Welche Versionen kann das Tool vergleichen?

Sie können das Tool verwenden, um eine beliebige Version von 2.x zu vergleichen.

## Wer kann das Upgrade-Kompatibilitäts-Tool 1.1.0 verwenden?

Adobe Commerce-Kunden.

## Installieren des Upgrade-Kompatibilitäts-Tools 1.1.0

Informationen zu Installationsschritten finden Sie unter Adobe Commerce: [Upgrade Compatibility Tool > Installieren](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/run) in unserer Entwicklerdokumentation. Informationen zu den Voraussetzungen für die Verwendung des Tools finden Sie unter Adobe Commerce: [Upgrade-Kompatibilitätstool](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/prerequisites) in unserer Entwicklerdokumentation.

## Wie lautet die Nummer neben den einzelnen Problemen?

Dies ist die Referenz für Fehlermeldungen, die Informationen zu Fehlern enthält, die beim Ausführen des Upgrade-Kompatibilitäts-Tools auftreten können.

Die Fehlermeldungen des Upgrade-Kompatibilitäts-Tools werden nach Ebene (kritische Probleme, Fehler und Warnungen) und Typ (Kern-Code, benutzerdefinierter Code und GraphQL-Schemata) kategorisiert. Jeder Typ enthält die folgenden Informationen:

* Fehlercode: Die von Adobe Commerce zugewiesene Kennung für die Fehlermeldung.
* Fehlerbeschreibung: Eine Beschreibung, die die Ursache des Fehlers zusammenfasst.
* Vorgeschlagene Fehleraktion: Falls zutreffend, bietet eine Anleitung zur Fehlerbehebung und -behebung.
* Die Codes werden auf der Seite [Fehlermeldungsreferenz“ ](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/reporting/error-messages).

## Wo kann ich Feedback zum Tool geben?

Sie können sich mit dem UCT-Team in unserem [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F) Slack-Kanal in Verbindung setzen. Wir freuen uns auf Ihr Feedback und Ihre Vorschläge zur Verbesserung des Tools.

## Verwandtes Lesen

* Adobe Commerce-Blog: [Einführung in das Upgrade-Kompatibilitäts-Tool (Alpha)](https://magento.com/blog/magento-news/introducing-upgrade-compatibility-tool)
* Adobe Commerce: [Upgrade-Kompatibilitätstool](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview) in unserer Entwicklerdokumentation.
