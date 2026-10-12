---
title: Problem mit GitHub-Token und wichtige Verfahren von Composer
description: Dieser Artikel enthält Lösungen für das Problem fehlgeschlagener Bereitstellungen im Zusammenhang mit GitHub-Token-Fehlern, die durch veraltete Composer-Schlüssel verursacht werden.
exl-id: 202cb936-f9ba-49ea-bf0a-6e6994d2337a
feature: Identity Management
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 23bc8570-95c6-5ef5-a563-2e4a4e6b4853
    internal-label: Identity Management
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '278'
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

Wenn diese Methode nicht funktioniert, reichen [ein Support-Ticket ein](https://experienceleague.adobe.com/de/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket).

## Verwandtes Lesen

* [GitHub-Blog: Hinter den neuen Authentifizierungstoken-Formaten von GitHub](https://github.blog/2021-04-05-behind-githubs-new-authentication-token-formats/)
* [InfoQ.com News-Artikel: GitHub ändert Token-Format zur Verbesserung der Identifizierbarkeit, des Scannens geheimer Daten und der Entropie](https://www.infoq.com/news/2021/04/github-new-token-format/)
