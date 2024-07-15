---
title: Installationsbefehl des Composers überschreibt .gitignore-Datei, Adobe Commerce
description: Dieser Artikel bietet eine Lösung für den Fall, dass eine verfolgte ".gitignore"-Datei vom Composer in Adobe Commerce in der Cloud-Infrastruktur 2.4.2-p1 und 2.3.7 überschrieben wird.
exl-id: b0604bae-d630-4292-88d7-6945db30fcf4
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Installationsbefehl des Composers überschreibt .gitignore-Datei, Adobe Commerce

Dieser Artikel bietet eine Lösung für den Fall, dass eine verfolgte `.gitignore` -Datei vom Composer in Adobe Commerce in der Cloud-Infrastruktur 2.4.2-p1 und 2.3.7 überschrieben wird.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur 2.4.2-p1 und 2.3.7.

## Problem

`.gitignore` -Datei wird überschrieben, wenn der Befehl zum Installieren von Composer ausgeführt wird.

<u>Zu reproduzierende Schritte</u>:


1. Erstellen Sie ein leeres Verzeichnis für Ihren Arbeitsbereich.
1. Führen Sie diesen Befehl im Stammverzeichnis aus:

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition:2.4.2-p1.
   ```

   \# oder 2.3.7

1. Führen Sie dann die folgenden Befehle aus:
   1. `echo "/this/line/should/stay" >> .gitignore`
   1. `git init`
   1. `git add * && git add .*`
   1. `git commit -m "Init"` # Datei zum Repo hinzugefügt
   1. `rm -rf vendor/*`
   1. `composer install`
   1. `git diff`

      ```git
      diff --git a/.gitignore b/.gitignore
      index c144521..7092a56 100644
      --- a/.gitignore
      +++ b/.gitignore
      @@ -70,4 +70,3 @@ atlassian*
      /generated/*
      !/generated/.htaccess
      .DS_Store
      -/this/line/should/stay
      ```

<u>Erwartetes Ergebnis</u>:

`.gitignore` wird vom Composer nicht überschrieben.

<u>Tatsächliches Ergebnis</u>:

`.gitignore` wird von jedem Komponenteninstallationsablauf überschrieben.

## Lösung

Um Ihre benutzerspezifische `.gitignore file` beizubehalten, müssen Sie sie im Abschnitt `magento-deploy-ignore` ignorieren.

```git
{
...
"extra": {
    "magento-deploy-ignore": {
        "*": [
            "/.gitignore"
        ]
    }
    ...
}
```


## Verwandtes Lesen

* [Getrackte .gitignore-Datei wird vom Composer überschrieben!](https://github.com/magento/magento2/issues/32888) in Magento2 GitHub.
