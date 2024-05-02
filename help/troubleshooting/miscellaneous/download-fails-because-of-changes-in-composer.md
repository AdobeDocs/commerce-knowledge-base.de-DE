---
title: Download schlägt aufgrund von Änderungen in Composer fehl
description: Dieser Artikel enthält eine Fehlerbehebung für einen fehlgeschlagenen Adobe Commerce-Download- und Ausnahmefehler.
exl-id: 5abdab97-4b0c-466b-a68f-a2637d2826e5
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# Download schlägt aufgrund von Änderungen in Composer fehl

Dieser Artikel enthält eine Fehlerbehebung für einen fehlgeschlagenen Adobe Commerce-Download- und Ausnahmefehler.

## Problem

Während des Downloads wird der folgende Fehler angezeigt:

```php
[ErrorException]
  file_get_contents(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory
```

## Ursache

Dies geschieht aufgrund von Änderungen in bestimmten Versionen von Composer. Die Lösung besteht darin, Composer auf eine frühere Version herabzustufen und den Adobe Commerce-Download erneut auszuführen.

## Lösung

Dieses Problem tritt in jeder Version des Composers auf, die vom 21. November bis 26. November 2015 datiert wurde. Um zu bestätigen, dass dieses Problem mit der Composer-Version in Verbindung steht, geben Sie den folgenden Befehl ein:

```php
composer -v
```

Die Version weist folgendes Format auf:

```php
Composer version 1.0-dev (2b14f0a047dd4f3545ec82381f65c36ea93a4c81) 2015-11-25 17:13:09
```

Beachten Sie, dass das Datum 2015-11-25 ist, was darauf hinweist, dass der Composer dieses Problem hat.

So umgehen Sie es:

1. Ändern Sie Ihre Version von Composer, damit Sie die Adobe Commerce-Software herunterladen können, indem Sie einen der folgenden Schritte ausführen:

   * Aktualisieren Sie Composer mit dem folgenden Befehl: `composer self-update 1.0.0-alpha11`.
   * Upgrade von Composer auf eine Version nach dem 26. November 2015: `composer self-update`.

1. Löschen Sie das Adobe Commerce-Verzeichnis und die Unterverzeichnisse.
1. Versuchen Sie den Download erneut mit `[composer create-project](https://devdocs.magento.com/guides/v2.3/install-gde/composer.html)` oder `[git clone](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/dev_install.html)`.
1. Nachdem Sie die Adobe Commerce-Software erfolgreich heruntergeladen haben, aktualisieren Sie Composer: `composer self-update`.
