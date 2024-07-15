---
title: Fehlerbehebung bei Problemen mit dem Upgrade-Kompatibilitätstool
description: In diesem Artikel werden Fehler erläutert, die bei der Verwendung des Upgrade-Kompatibilitätstools auftreten können, und es werden Lösungen zur Behebung dieser Fehler bereitgestellt, damit Sie das Tool erfolgreich ausführen können.
exl-id: 1cce1146-942e-46cb-a395-8da9e472cd39
feature: Customer Service, Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Fehlerbehebung bei Problemen mit dem Upgrade-Kompatibilitätstool

In diesem Artikel werden Fehler erläutert, die bei der Verwendung des Upgrade-Kompatibilitätstools auftreten können, und es werden Lösungen zur Behebung dieser Fehler bereitgestellt, damit Sie das Tool erfolgreich ausführen können.

## Betroffene Produkte und Versionen

* [Upgrade-Kompatibilitätstool](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview.html) ist ab Version 2.3.0 mit Adobe Commerce-Versionen kompatibel.

## Fehler bei Segmentierung

<u>Ursache</u>:

Wenn zwei Module denselben Namen haben, zeigt das Upgrade-Kompatibilitätstool einen Segmentierungsfehler an.

<u>Lösung</u>:

Um diesen Fehler zu vermeiden, wird empfohlen, den Pfad zum Modul als Argument anzugeben:

```bash
bin/uct upgrade:check --current-version=2.4.4 path/to/the/module
```

>[!WARNING]
>
> Das Upgrade-Kompatibilitätstool kann die Codebase möglicherweise nicht analysieren, wenn es eine zirkuläre Abhängigkeit zwischen den Methoden enthält.

## Leere Ausgabe

<u>Zu reproduzierende Schritte</u>:

1. Wenn dieser Befehl nach der Ausführung ausgeführt wurde:

   ```bash
   bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
   ```

1. Die einzige Ausgabe ist `Upgrade compatibility tool`:

   ```terminal
   bin/uct upgrade:check /var/www/project/magento/ -c 2.4.1
   Upgrade compatibility tool
   ```

<u>Ursache</u>:

Die wahrscheinliche Ursache ist eine PHP-Speicherbegrenzung.

Es gibt zwei mögliche Lösungen, um diese PHP-Speicherbegrenzung zu vermeiden.

<u>Lösung 1</u>:

Überschreiben Sie die Speicherbegrenzung, indem Sie `memory_limit` auf `-1` setzen:

```bash
php -d memory_limit=-1 /bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```

>[!NOTE]
>
> Die `M2_VERSION` ist die Adobe Commerce-Zielversion, die Sie mit Ihrer Adobe Commerce-Instanz vergleichen möchten.

<u>Lösung 2</u>:

Durch Hinzufügen der Option `-m` kann das Upgrade-Kompatibilitätstool jedes einzelne Modul unabhängig analysieren, um zu vermeiden, dass in Ihrer Adobe Commerce-Instanz zwei Module mit demselben Namen auftreten.

Mit dieser Befehlsoption kann das Upgrade-Kompatibilitätstool auch einen Ordner analysieren, der mehrere Module enthält:

```bash
bin/uct upgrade:check /<dir>/<instance-name> -m /vendor/<vendor-name>/
```

Weitere Informationen zu Befehlszeilenoberflächenoptionen finden Sie auf der Seite [Ausführen des Tools in einer Befehlszeilenschnittstelle ](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/run.html) .
