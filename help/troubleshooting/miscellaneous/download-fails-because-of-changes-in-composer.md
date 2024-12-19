---
title: Der Download schlägt aufgrund von Änderungen im Composer fehl
description: Dieser Artikel enthält eine Fehlerbehebung für einen fehlgeschlagenen Adobe Commerce-Download und einen Ausnahmefehler.
exl-id: 5abdab97-4b0c-466b-a68f-a2637d2826e5
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# Der Download schlägt aufgrund von Änderungen im Composer fehl

Dieser Artikel enthält eine Fehlerbehebung für einen fehlgeschlagenen Adobe Commerce-Download und einen Ausnahmefehler.

## Problem

Während des Downloads wird der folgende Fehler angezeigt:

```php
[ErrorException]
  file_get_contents(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory
```

## Ursache

Dies geschieht aufgrund von Änderungen in bestimmten Versionen von Composer. Die Problemumgehung besteht darin, Composer auf eine frühere Version herunterzuladen und den Adobe Commerce-Download erneut zu versuchen.

## Lösung

Jede Version von Composer datiert zwischen 21. November und 26. November 2015 hat dieses Problem. Um zu bestätigen, dass dieses Problem mit der Composer-Version zusammenhängt, geben Sie den folgenden Befehl ein:

```php
composer -v
```

Die Version wird ähnlich der folgenden angezeigt:

```php
Composer version 1.0-dev (2b14f0a047dd4f3545ec82381f65c36ea93a4c81) 2015-11-25 17:13:09
```

Beachten Sie, dass das Datum 2015-11-25 ist, was darauf hinweist, dass Composer dieses Problem hat.

So umgehen Sie das Problem:

1. Ändern Sie Ihre Composer-Version, um die Adobe Commerce-Software herunterladen zu können, indem Sie einen der folgenden Schritte ausführen:

   * Downgrade Composer mit dem folgenden Befehl: `composer self-update 1.0.0-alpha11`.
   * Aktualisieren Sie Composer auf eine Version nach dem 26. November 2015: `composer self-update`.

1. Löschen Sie das Adobe Commerce-Verzeichnis und die Unterverzeichnisse.
1. Versuchen Sie den Download erneut mit `[composer create-project](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/composer)` oder `[git clone](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)`.
1. Nachdem Sie die Adobe Commerce-Software erfolgreich heruntergeladen haben, aktualisieren Sie Composer: `composer self-update`.
