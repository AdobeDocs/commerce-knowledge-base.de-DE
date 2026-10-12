---
title: Composer-Installationsbefehl überschreibt .gitignore-Datei, Adobe Commerce
description: Dieser Artikel bietet eine Lösung für den Fall, dass eine verfolgte Datei ".gitignore“ von Composer in Adobe Commerce unter den Cloud-Infrastrukturen 2.4.2-p1 und 2.3.7 überschrieben wird.
exl-id: b0604bae-d630-4292-88d7-6945db30fcf4
feature: Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%
---
# Composer-Installationsbefehl überschreibt .gitignore-Datei, Adobe Commerce

Dieser Artikel bietet eine Lösung für den Fall, dass eine verfolgte `.gitignore`-Datei von Composer in Adobe Commerce auf Cloud-Infrastrukturen 2.4.2-p1 und 2.3.7 überschrieben wird.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur 2.4.2-p1 und 2.3.7.

## Problem

`.gitignore` Datei wird überschrieben, wenn der Composer-Installationsbefehl ausgeführt wird.

<u>Schritte zur Reproduktion</u>:


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
   1. `git commit -m "Init"` # Datei in Repository übertragen
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

`.gitignore` wird nicht vom Komponisten überschrieben.

<u>Tatsächliches </u>:

`.gitignore` wird von jeder Composer-Installationsausführung überschrieben.

## Lösung

Um Ihre benutzerdefinierten `.gitignore file` beizubehalten, müssen Sie sie im `magento-deploy-ignore` Abschnitt ignorieren.

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
