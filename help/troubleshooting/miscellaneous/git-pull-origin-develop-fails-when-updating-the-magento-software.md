---
title: Die Git-Pull-Entwicklung schlägt beim Aktualisieren der Adobe Commerce-Software fehl
description: Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass Sie die Adobe Commerce-Software nicht aktualisieren können, wenn Sie „git pull origin develop“ ausführen.
exl-id: b133253e-c160-4f15-a9b0-8591e93a1e9b
feature: Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%
---
# Die Git-Pull-Entwicklung schlägt beim Aktualisieren der Adobe Commerce-Software fehl

Dieser Artikel bietet eine Fehlerbehebung für den Fall, dass Sie die Adobe Commerce-Software nicht aktualisieren können, wenn Sie `git pull origin develop` ausführen.

## Details

Um die Adobe Commerce-Software zu aktualisieren, müssen Sie unter anderem Ihr lokales Repository aktualisieren, indem Sie Folgendes ausführen:

```bash
$ git pull origin develop
```

Der folgende Fehler kann angezeigt werden:

```bash
error: Your local changes to the following files would be overwritten by merge:
<list of files>
```

Um herauszufinden, welche Dateien überschrieben werden können, lesen Sie entweder die Meldung oder geben Sie Folgendes ein:

```bash
git status
```

Im nächsten Abschnitt finden Sie Lösungsvorschläge.

### Lösungsvorschläge

Ihre Lösung hängt davon ab, ob Sie Dateien im Adobe Commerce-Dateisystem absichtlich geändert haben oder nicht. Weitere Informationen finden Sie in einem der folgenden Abschnitte.

#### Sie haben Dateien absichtlich geändert

Die Konflikte manuell auf die übliche Weise lösen. Wenn Sie sich nicht sicher sind, was Sie tun sollen, konsultieren Sie [GitHub-Hilfe](https://help.github.com/).

#### Sie haben keine Dateien absichtlich geändert

Probieren Sie einen der folgenden Schritte aus:

* Wenn Sie sicher sind, dass Sie keine Dateien geändert haben, und es Ihnen nichts ausmacht, die Änderungen im Adobe Commerce-Dateisystem zu entfernen oder zu überschreiben, geben Sie Folgendes ein:

  </p>
    <pre><code class="language-bash">$ git reset --hard HEAD && git pull origin develop</code></pre>

  Fahren Sie anschließend mit dem Adobe Commerce-Update dort fort, wo Sie aufgehört haben.

* Es ist möglich, dass eine GitHub-Konfigurationseinstellung diese Fehler in Zukunft verhindern kann. Standardmäßig speichert GitHub Inhalte unter Verwendung der vom Betriebssystem vorgegebenen Zeilenendzeichen. Wenn Sie Linux verwenden, aber ein anderer Mitarbeiter eine Änderung mithilfe von Windows vorgenommen hat, konvertiert GitHub die Windows-Zeilenenden beim Klonen oder Abrufen in Linux. Dadurch sieht es so aus, als ob die Dateien geändert wurden, obwohl eigentlich keine Änderung vorgenommen wurde.

  Um GitHub so zu konfigurieren, dass Zeilenenden ignoriert werden, geben Sie den folgenden Befehl in Ihren Git-Client ein:

  </p>
    <pre><code class="language-bash">$ git config --system core.autocrlf false</code></pre>

  Wenn Sie Windows verwenden, geben Sie Folgendes ein:

  </p>
    <pre><code class="language-bash">$ git config --system core.eol LF</code></pre>

  >[!NOTE]
  >
  >Adobe empfiehlt oder unterstützt keine bestimmten GitHub-Konfigurationseinstellungen. Die zuvor genannten Vorschläge sind nur Empfehlungen. Weitere Informationen finden Sie in der [GitHub-Hilfe](https://help.github.com/).

  Fahren Sie mit dem Adobe Commerce-Update dort fort, wo Sie aufgehört haben.
