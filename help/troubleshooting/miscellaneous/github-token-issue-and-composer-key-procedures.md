---
title: Problem mit GitHub-Token und wichtige Verfahren von Composer
description: Dieser Artikel enthält Lösungen für das Problem fehlgeschlagener Bereitstellungen im Zusammenhang mit GitHub-Token-Fehlern, die durch veraltete Composer-Schlüssel verursacht werden.
exl-id: 202cb936-f9ba-49ea-bf0a-6e6994d2337a
feature: Identity Management
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Problem mit GitHub-Token und wichtige Verfahren von Composer

Dieser Artikel enthält Lösungen für das Problem fehlgeschlagener Bereitstellungen im Zusammenhang mit GitHub-Token-Fehlern, die durch veraltete Composer-Schlüssel verursacht werden.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur, [alle unterstützten Versionen](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Composer-Versionen 1.10.20 und niedriger

>[!NOTE]
>
>Adobe Commerce-Händler vor Ort sollten sich bei ihrem Hostanbieter erkundigen, ob sie Composer Version 1.10.21 oder höher aufgrund der von Git eingeführten Änderungen des Token-Formats verwenden.

## Problem

Bereitstellungen schlagen fehl und Bereitstellungsprotokolle enthalten Informationen ähnlich den folgenden:

*Schwerwiegender Fehler: UnexpectedValueException: Ihr GitHub-OAuth-Token für github.com enthält ungültige Zeichen: „ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx“ in /app/vendor/composer/composer/src/Composer/IO/BaseIO.php:129*

## Ursache

Veraltete Composer-Schlüssel verursachen die GitHub-Token-Fehler, die zu fehlgeschlagenen Bereitstellungen führen.

## Lösung

Um das Problem zu beheben, aktualisieren Sie Ihre Composer-Version auf 1.10.22:

1. Führen Sie in Ihrer lokalen Umgebung `composer require “composer/composer”:”>1.10.21` aus.
1. Dadurch wird die Anforderung für diese Composer-Paketversion hinzugefügt. Überprüfen Sie die Sperrdatei - `composer/composer` Version muss 1.0.22 oder höher sein.
1. `composer.json` und `composer.lock` übertragen und eine Bereitstellung per Push übertragen.

Wenn diese Methode nicht funktioniert, reichen [ein Support-Ticket ein](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Verwandtes Lesen

* [GitHub-Blog: Hinter den neuen Authentifizierungstoken-Formaten von GitHub](https://github.blog/2021-04-05-behind-githubs-new-authentication-token-formats/)
* [InfoQ.com News-Artikel: GitHub ändert Token-Format, um die Identifizierbarkeit, das Scannen geheimer Daten und die Entropie zu verbessern](https://www.infoq.com/news/2021/04/github-new-token-format/)
