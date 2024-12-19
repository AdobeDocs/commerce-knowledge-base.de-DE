---
title: Abgelaufene „oauth_tokens“ vor dem Upgrade auf 2.4.6 reduzieren
description: Dieser Artikel bietet eine Lösung für das Problem, dass in Ihrer Tabelle „oauth_token“ eine große Anzahl von „oauth_token“ angezeigt wird, was zu einer langen Verzögerung beim Upgrade auf Version 2.4.6 führen kann. Es wird empfohlen, die Tabelle „oauth_token“ mit CleanExpiredTokens.php zu reduzieren.
feature: Variables, Upgrade
role: Developer
exl-id: 92d1d15a-04da-4ba4-b6b8-5c491af9c4c1
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# Reduzieren abgelaufener `oauth_tokens` vor dem Upgrade auf 2.4.6

Dieser Artikel bietet eine Lösung für das Problem, dass eine große Anzahl von `oauth_tokens` in Ihrer `oauth_token` angezeigt wird, was zu einer langen Verzögerung beim Upgrade auf Version 2.4.6 führen kann. Es wird empfohlen, die `oauth_token` mithilfe des [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php)-[!DNL cron]-Auftrags zu reduzieren, um die abgelaufenen Token zu löschen.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.4.0 - 2.4.6, alle Bereitstellungsmethoden

## Problem

Wenn Ihre `oauth_token` eine große Anzahl von `oauth_tokens` enthält, kann dies zu einer langen Verzögerung beim Upgrade auf Version 2.4.6 führen.

Der Upgrade-Prozess umfasst die Verschlüsselung dieser Token für eine zusätzliche Sicherheitsebene, und es werden nur 100 Datensätze gleichzeitig verarbeitet. Dies kann bei einer großen Anzahl von Token mehrere Stunden dauern.

Wenn Sie eine große Anzahl von `oauth_tokens` in Ihrer `oauth_token`-Tabelle reduzieren, kann eine lange Verzögerung beim Upgrade auf Version 2.4.6 verhindert werden.

## Lösung

Stellen Sie vor dem Start eines Upgrades zunächst sicher, dass der [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] ausgeführt wird. Die Größe der `oauth_token` wird reduziert, indem die abgelaufenen `oauth_tokens`-Token gelöscht werden. Standardmäßig sollte die Tabelle bereits aktiviert sein.

Führen Sie Folgendes aus, um den [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php)-[!DNL cron]-Auftrag manuell Trigger:
```bin/magento cron:run --group=default```

## Verwandtes Lesen

* [Services > [!DNL OAuth]](https://experienceleague.adobe.com/docs/commerce-admin/config/services/oauth.html) im Commerce-Konfigurationshandbuch
* [Authentifizierungshandbuch](https://developer.adobe.com/developer-console/docs/guides/authentication/) im Adobe Developer-Handbuch
* [Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook
