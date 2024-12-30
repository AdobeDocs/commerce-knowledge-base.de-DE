---
title: Fehlerbehebung bei Fehlern des Kompatibilitäts-Tools für Upgrades
description: In diesem Artikel werden Fehler erläutert, die bei der Verwendung des Upgrade-Kompatibilitäts-Tools auftreten können, und Lösungen bereitgestellt, mit denen diese Fehler behoben werden können, damit Sie das Tool erfolgreich ausführen können.
exl-id: 1cce1146-942e-46cb-a395-8da9e472cd39
feature: Customer Service, Install, Upgrade
role: Developer
source-git-commit: 35d4f2130d0ec71f71f5f20aa8a7c76207e7a35a
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Fehlerbehebung bei Fehlern des Kompatibilitäts-Tools für Upgrades

In diesem Artikel werden Fehler erläutert, die bei der Verwendung des Upgrade-Kompatibilitäts-Tools auftreten können, und Lösungen bereitgestellt, mit denen diese Fehler behoben werden können, damit Sie das Tool erfolgreich ausführen können.

## Betroffene Produkte und Versionen

* [Upgrade-Kompatibilitätstool](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview.html) ist ab Version 2.3.0 mit Adobe Commerce kompatibel.

## Fehler bei Segmentierungsfehler

<u>Ursache</u>:

Wenn zwei Module denselben Namen haben, zeigt das Upgrade-Kompatibilitäts-Tool einen Segmentierungsfehler an.

<u>Lösung</u>:

Um diesen Fehler zu vermeiden, wird empfohlen, den Pfad zum -Modul als Argument anzugeben:

```bash
bin/uct upgrade:check --current-version=2.4.4 path/to/the/module
```

>[!WARNING]
>
> Das Upgrade-Kompatibilitäts-Tool kann die Codebasis möglicherweise nicht analysieren, wenn sie eine zirkuläre Abhängigkeit zwischen Methoden enthält.

## Leere Ausgabe

<u>Schritte zur Reproduktion</u>:

1. Wenn nach Ausführung dieses Befehls:

   ```bash
   bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
   ```

1. Die einzige Ausgabe ist `Upgrade compatibility tool`:

   ```bash
   bin/uct upgrade:check /var/www/project/magento/ -c 2.4.1
   Upgrade compatibility tool
   ```

<u>Ursache</u>:

Die wahrscheinliche Ursache ist eine PHP-Speicherbegrenzung.

Es gibt zwei mögliche Lösungen, um diese PHP Speicherbegrenzung zu vermeiden.

<u>Lösung </u>:

Überschreiben Sie die Speicherbegrenzung, indem Sie `memory_limit` auf `-1` setzen:

```bash
php -d memory_limit=-1 /bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```

>[!NOTE]
>
> Die `M2_VERSION` ist die Adobe Commerce-Zielversion, die Sie mit Ihrer Adobe Commerce-Instanz vergleichen möchten.

<u>Lösung </u>:

Durch Hinzufügen der `-m` Option kann das Upgrade-Kompatibilitäts-Tool jedes einzelne Modul unabhängig analysieren, um zu vermeiden, dass zwei Module mit demselben Namen in Ihrer Adobe Commerce-Instanz auftreten.

Diese Befehlsoption ermöglicht es dem Upgrade-Kompatibilitäts-Tool auch, einen Ordner zu analysieren, der mehrere Module enthält:

```bash
bin/uct upgrade:check /<dir>/<instance-name> -m /vendor/<vendor-name>/
```

Weitere [ zu den Optionen für die Befehlszeilenschnittstelle finden Sie ](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/run.html) Seite Ausführen des Tools in einer Befehlszeilenschnittstelle .
