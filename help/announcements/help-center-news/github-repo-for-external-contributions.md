---
title: Adobe Commerce-Support-Wissensdatenbank beginnt mit der Annahme von Beiträgen
description: Ab dem 15. Juni akzeptiert das Knowledge Base-Team der Adobe Commerce-Support direkte Bearbeitungen und neue Artikelbeiträge von externer Adobe Commerce-Community über das [magento/Knowledgebase](https://github.com/magento/knowledge-base) GitHub-Repository!
exl-id: b5198de0-d6b5-4107-8b74-a12606583596
feature: Support
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# Adobe Commerce-Support-Wissensdatenbank beginnt mit der Annahme von Beiträgen

Ab dem 15. Juni akzeptiert das Knowledge Base-Team von Adobe Commerce direkt Bearbeitungen und neue Artikelbeiträge von externer Adobe Commerce-Community über das GitHub-Repository [magento/Knowledgebase](https://github.com/magento/knowledge-base)!

Haben Sie einen Tippfehler in einem unserer Artikel oder unvollständige Schritte zur Fehlerbehebung bemerkt?
Jetzt können Sie es selbst beheben und Beitragspunkte abrufen!

## Contribute

Wir freuen uns über alle möglichen Beiträge, von kleinen Tippkorrekturen bis hin zu kompletten Artikeln zur Fehlerbehebung. Wenn Sie zu diesem Repo beitragen, erhalten Sie Belohnungspunkte, die in etwa dem Adobe Commerce-Code und unserer Entwicklerdokumentation entsprechen. Weitere Informationen finden Sie unter [Beitragsbelohnungspunkte](https://github.com/magento/knowledge-base/blob/main/docs/contribution-points.md) .

### Allgemeiner Beitragsfluss

1. Fork diesen Repo.
1. Bearbeiten Sie das abgespaltete Repo.
1. Senden Sie eine Pull-Anfrage (PR) an dieses Repo.
1. Tests werden ausgeführt:
   * Adobe CLA - Sicherstellen, dass die Adobe Open Source Contributor License Agreement (Lizenzvereinbarung für-Mitarbeiter) unterzeichnet ist.
   * Markdown-Linktest: Stellen Sie sicher, dass die Markdown-Syntax korrekt ist.
   * Validierungstest für Dateistruktur : Stellen Sie sicher, dass der Commit gemäß der [erforderlichen Dateistruktur](https://github.com/magento/knowledge-base/blob/main/.github/CONTRIBUTING.md#file_structure) ausgeführt wird.
1. PR-Genehmigungsfluss:
   1. Die Entwickler der Support-Wissensdatenbank (KB) überprüfen die PR innerhalb mehrerer Tage und fügen Beschriftungen hinzu.
   1. KB-Autor kann Änderungen genehmigen/ablehnen/anfordern.
   1. Wenn es genehmigt wurde, fügt KB-Autor Beschriftungen hinzu, die dem in PR bereitgestellten Input entsprechen, und interne Subject Matter Expert (SME) überprüft die PR.
   1. KMU können Änderungen genehmigen/ablehnen/beantragen.
1. Sobald alle Korrekturen durchgeführt wurden (falls angefordert) und sowohl der KB-Autor als auch das KMU die PR genehmigen, importiert der KB-Autor Inhalte in das interne Repo und führt sie intern zusammen.
1. Das Repo [magento/Knowledgebase](https://github.com/magento/knowledge-base) synchronisiert sich innerhalb von 20 Minuten mit dem internen.
1. Sobald die Berichte synchronisiert sind, wird Ihr PR geschlossen und Sie erhalten [Beitragspunkte](#contribution-points).

Weitere Informationen zum Beitragsfluss finden Sie im [Mitarbeiter-Handbuch](https://github.com/magento/knowledge-base/blob/main/.github/CONTRIBUTING.md).
Vorlagen, Stilhandbücher und Formatierungsrichtlinien finden Sie in der [Dokumentation](https://github.com/magento/knowledge-base/tree/main/docs).

### Suchen Sie die Support-KB-Artikeldatei auf GitHub

In der Support-Wissensdatenbank (KB) sind Artikel in Abschnitte unterteilt, die unter Kategorien verschachtelt sind.

Beispielsweise gehört der Artikel [How to subscribe to Adobe Magento status updates](/help/how-to/general/how-to-subscribe-to-adobe-magento-status-updates.md) zum Abschnitt &quot;General&quot;in der Kategorie &quot;How To&quot;.

Sie können den Abschnitt- und Kategorienamen im Breadcrumbs-Pfad auf der Artikelseite sehen, siehe Abbildung unten:

![Kategorie und Abschnitt-Breadcrumbs](assets/breadcrumbs.png)

Artikeldateien sind im Repo [magento/Knowledge-base](https://github.com/magento/knowledge-base) auf die gleiche Weise organisiert.
Der gesamte Inhalt wird im Ordner &quot;`src`&quot;gespeichert, wobei Ordner für Kategorien und verschachtelte Ordner für Abschnitte stehen. Dateinamen fallen entweder mit Artikeltiteln zusammen oder sind ähnlich.

Sie können auch die Suche innerhalb des Repositorys verwenden, indem Sie einen Textabschnitt aus dem Support-KB-Artikel als Suchzeichenfolge verwenden. Wenn die Suche Dateien zurückgibt, die diese Zeichenfolge enthalten, wählen Sie die Datei aus, die zum richtigen Abschnitt und zur richtigen Kategorie gehört.

### Beitragspunkte

Das Repository [magento/Knowledgebase](https://github.com/magento/knowledge-base) ist in das Magento Community Engineering integriert, um Beitragspunkte und Support zu erhalten.

Im Dokument [Beitragspunkte](https://github.com/magento/knowledge-base/blob/main/docs/contribution-points.md) erfahren Sie, wie Punkte belohnt werden.
