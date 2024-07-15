---
title: GitHub-Token-Problem und wichtige Verfahren für Composer
description: Dieser Artikel enthält Lösungen für das Problem fehlgeschlagener Bereitstellungen im Zusammenhang mit Github-Token-Fehlern, die durch veraltete Composer-Schlüssel verursacht werden.
exl-id: 202cb936-f9ba-49ea-bf0a-6e6994d2337a
feature: Identity Management
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# GitHub-Token-Problem und wichtige Verfahren für Composer

Dieser Artikel enthält Lösungen für das Problem fehlgeschlagener Bereitstellungen im Zusammenhang mit Github-Token-Fehlern, die durch veraltete Composer-Schlüssel verursacht werden.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, [alle unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Composer-Versionen 1.10.20 und niedriger

>[!NOTE]
>
>Vor Ort sollten sich Adobe Commerce-Händler bei ihrem Host-Provider erkundigen, ob sie Composer der Version 1.10.21 oder höher verwenden, da Git Änderungen am Tokenformat vornimmt.

## Problem

Bereitstellungsprotokolle schlagen fehl und enthalten Informationen ähnlich den folgenden:

*Schwerwiegender Fehler: Uncaught UnexpectedValueException: Ihr github-Oauth-Token für github.com enthält ungültige Zeichen: &quot;ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx&quot; in /app/vendor/composer/composer/src/Composer/IO/BaseIO.php:129*

## Ursache

Veraltete Composer-Schlüssel verursachen Github-Token-Fehler, die zu fehlgeschlagenen Bereitstellungen führen.

## Lösung

Um das Problem zu beheben, aktualisieren Sie Ihre Composer-Version auf Version 1.10.22:

1. Führen Sie in Ihrer lokalen Umgebung `composer require “composer/composer”:”>1.10.21` aus.
1. Dadurch wird die Anforderung für diese Composer-Paketversion hinzugefügt. Überprüfen Sie die Sperrdatei - die Version `composer/composer` muss 1.0.22 oder höher sein.
1. Setzen Sie `composer.json` und `composer.lock` ein und führen Sie eine Bereitstellung durch.

Wenn diese Methode nicht funktioniert, senden Sie bitte [ein Support-Ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Verwandtes Lesen

* [GitHub-Blog: Hinter den neuen Authentifizierungstoken-Formaten von GitHub](https://github.blog/2021-04-05-behind-githubs-new-authentication-token-formats/)
* [InfoQ.com News-Artikel: GitHub-Änderungs-Token-Format zur Verbesserung der Identifizierbarkeit, geheimen Scannen und Entropie](https://www.infoq.com/news/2021/04/github-new-token-format/)
