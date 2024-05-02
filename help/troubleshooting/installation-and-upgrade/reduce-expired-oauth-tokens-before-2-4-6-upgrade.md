---
title: Löschen Sie abgelaufene `oauth_tokens` vor der Aktualisierung 2.4.6
description: Dieser Artikel bietet eine Lösung für das Problem, dass in Ihrer Tabelle "oauth_token"eine große Anzahl von "oauth_token"vorhanden ist, was zu einer langen Verzögerung bei der Aktualisierung auf Version 2.4.6 führen kann. Es wird empfohlen, die Tabelle "oauth_token"mit CleanExpiredTokens.php zu reduzieren.
feature: Variables, Upgrade
role: Developer
exl-id: 92d1d15a-04da-4ba4-b6b8-5c491af9c4c1
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# Abgelaufene reduzieren `oauth_tokens` vor der Aktualisierung 2.4.6

Dieser Artikel bietet eine Lösung für das Problem, bei dem eine große Anzahl von `oauth_tokens` in `oauth_token` -Tabelle, was eine lange Verzögerung bei der Aktualisierung auf Version 2.4.6 verursachen kann. Es wird empfohlen, die `oauth_token` -Tabelle mithilfe der [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] Auftrag zum Löschen der abgelaufenen Token.

## Betroffene Produkte und Versionen

* Adobe Commerce 2.4.0 - 2.4.6, alle Bereitstellungsmethoden

## Problem

Wenn eine große Anzahl von `oauth_tokens` in `oauth_token` -Tabelle, die eine lange Verzögerung bei der Aktualisierung auf Version 2.4.6 verursachen kann.

Der Aktualisierungsprozess umfasst die Verschlüsselung dieser Token für eine zusätzliche Sicherheitsschicht, und es werden nur 100 Datensätze gleichzeitig erstellt. Dies kann mehrere Stunden dauern, wenn eine große Anzahl von Token vorhanden ist.

Eine große Anzahl von `oauth_tokens` in `oauth_token` -Tabelle kann eine lange Verzögerung bei der Aktualisierung auf Version 2.4.6 verhindern.

## Lösung

Bevor Sie ein Upgrade starten, stellen Sie zunächst sicher, dass die [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] Auftrag wird ausgeführt. Dadurch wird die Größe der `oauth_token` -Tabelle durch Löschen des abgelaufenen `oauth_tokens` -Token und sollten bereits standardmäßig aktiviert sein.

So erstellen Sie manuell den Trigger [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] Auftrag, ausführen:
```bin/magento cron:run --group=default```

## Verwandtes Lesen

* [Dienste > [!DNL OAuth]](https://experienceleague.adobe.com/docs/commerce-admin/config/services/oauth.html) im Handbuch zur Commerce-Konfigurationsreferenz.
* [Authentifizierungshandbuch](https://developer.adobe.com/developer-console/docs/guides/authentication/) im Adobe Developer-Handbuch.
