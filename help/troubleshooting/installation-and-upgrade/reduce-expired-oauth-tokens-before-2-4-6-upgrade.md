---
title: Löschen Sie abgelaufene `oauth_tokens` vor der Aktualisierung 2.4.6
description: Dieser Artikel bietet eine Lösung für das Problem, dass in Ihrer Tabelle "oauth_token"eine große Anzahl von "oauth_token"vorhanden ist, was zu einer langen Verzögerung bei der Aktualisierung auf Version 2.4.6 führen kann. Es wird empfohlen, die Tabelle "oauth_token"mit CleanExpiredTokens.php zu reduzieren.
feature: Variables, Upgrade
role: Developer
exl-id: 92d1d15a-04da-4ba4-b6b8-5c491af9c4c1
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# Verkleinern abgelaufener `oauth_tokens` vor der Aktualisierung 2.4.6

Dieser Artikel bietet eine Lösung für das Problem, dass in Ihrer `oauth_token` -Tabelle eine große Anzahl von `oauth_tokens` vorhanden ist, was zu einer langen Verzögerung bei der Aktualisierung auf Version 2.4.6 führen kann. Es wird empfohlen, die Tabelle `oauth_token` mit dem Auftrag [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] zu reduzieren, um die abgelaufenen Token zu löschen.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.4.0 - 2.4.6, alle Bereitstellungsmethoden

## Problem

Wenn Ihre `oauth_token` -Tabelle eine große Anzahl von `oauth_tokens` enthält, kann dies zu einer langen Verzögerung bei der Aktualisierung auf Version 2.4.6 führen.

Der Aktualisierungsprozess umfasst die Verschlüsselung dieser Token für eine zusätzliche Sicherheitsschicht, und es werden nur 100 Datensätze gleichzeitig erstellt. Dies kann mehrere Stunden dauern, wenn eine große Anzahl von Token vorhanden ist.

Wenn Sie eine große Anzahl von `oauth_tokens` in Ihrer `oauth_token`-Tabelle reduzieren, kann dies eine lange Verzögerung bei der Aktualisierung auf Version 2.4.6 verhindern.

## Lösung

Bevor Sie ein Upgrade starten, stellen Sie zunächst sicher, dass der Auftrag [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] ausgeführt wird. Dadurch wird die Größe der Tabelle `oauth_token` verringert, indem die abgelaufenen `oauth_tokens` -Token gelöscht werden. Diese sollten bereits standardmäßig aktiviert sein.

Um den Auftrag [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] manuell Trigger, führen Sie Folgendes aus:
```bin/magento cron:run --group=default```

## Verwandtes Lesen

* [Dienste > [!DNL OAuth]](https://experienceleague.adobe.com/docs/commerce-admin/config/services/oauth.html) im Commerce Configuration Reference Guide
* [Authentifizierungshandbuch](https://developer.adobe.com/developer-console/docs/guides/authentication/) im Adobe Developer-Handbuch
* [Best Practices für die Änderung von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Playbook für die Commerce-Implementierung
