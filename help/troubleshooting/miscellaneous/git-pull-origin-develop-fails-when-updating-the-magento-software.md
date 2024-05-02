---
title: Die Entwicklung der Git-Pull-Herkunft schlägt bei der Aktualisierung der Adobe Commerce-Software fehl
description: Dieser Artikel enthält eine Fehlerbehebung für Fälle, in denen Sie die Adobe Commerce-Software nicht aktualisieren können, wenn Sie "Git Pull Origin Development"ausführen.
exl-id: b133253e-c160-4f15-a9b0-8591e93a1e9b
feature: Upgrade
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Die Entwicklung der Git-Pull-Herkunft schlägt bei der Aktualisierung der Adobe Commerce-Software fehl

Dieser Artikel enthält eine Fehlerbehebung für Fälle, in denen Sie Adobe Commerce-Software bei der Ausführung nicht aktualisieren können `git pull origin develop`.

## Details

Eine der Schritte zum Aktualisieren der Adobe Commerce-Software besteht darin, Ihr lokales Repository zu aktualisieren, indem Sie Folgendes ausführen:

```bash
$ git pull origin develop
```

Der folgende Fehler könnte angezeigt werden:

```terminal
error: Your local changes to the following files would be overwritten by merge:
<list of files>
```

Um festzustellen, welche Dateien überschrieben werden können, lesen Sie die Nachricht oder geben Sie Folgendes ein:

```bash
git status
```

Im nächsten Abschnitt werden die vorgeschlagenen Lösungen erläutert.

### Empfohlene Lösungen

Ihre Lösung hängt davon ab, ob Sie absichtlich Dateien im Adobe Commerce-Dateisystem geändert haben oder nicht. Weitere Informationen finden Sie in einem der folgenden Abschnitte.

#### Absichtlich geänderte Dateien

Beheben Sie die Konflikte manuell auf die übliche Weise. Wenn Sie sich nicht sicher sind, was zu tun ist, konsultieren Sie [GitHub-Hilfe](https://help.github.com/).

#### Sie haben keine Dateien absichtlich geändert

Versuchen Sie Folgendes:

* Wenn Sie sicher sind, dass Sie keine Dateien geändert haben und es Sie nicht stört, die Änderungen im Adobe Commerce-Dateisystem zu entfernen oder zu überschreiben, geben Sie Folgendes ein:

  </p>
    <pre><code class="language-bash">$ git reset --hard HEAD && git pull origin develop</code></pre>

  Danach fahren Sie mit dem Adobe Commerce-Update fort, wo Sie aufgehört haben.

* Es ist möglich, dass eine GitHub-Konfigurationseinstellung diese Fehler in Zukunft verhindern kann. Standardmäßig speichert GitHub Inhalte mithilfe der standardmäßigen Zeilenendzeichen des Betriebssystems. Wenn Sie Linux verwenden, aber ein anderer Mitarbeiter eine Änderung mit Windows vorgenommen hat, konvertiert GitHub die Windows-Zeilenendungen beim Klonen oder Pull in Linux. Dadurch entsteht das Erscheinungsbild einer Änderung an Dateien, wenn tatsächlich keine Änderung vorgenommen wurde.

  Um GitHub so zu konfigurieren, dass Zeilenende ignoriert werden, geben Sie den folgenden Befehl in Ihren Git-Client ein:

  </p>
    <pre><code class="language-bash">$ git config --system core.autocrlf false</code></pre>

  Wenn Sie Windows verwenden, geben Sie Folgendes ein:

  </p>
    <pre><code class="language-bash">$ git config --system core.eol LF</code></pre>

  >[!NOTE]
  >
  >Adobe empfiehlt oder unterstützt keine bestimmten GitHub-Konfigurationseinstellungen. Die vorhergehenden sind nur Vorschläge. Weitere Informationen finden Sie unter [GitHub-Hilfe](https://help.github.com/).

  Fahren Sie mit Ihrem Adobe Commerce-Update fort, wo Sie aufgehört haben.
