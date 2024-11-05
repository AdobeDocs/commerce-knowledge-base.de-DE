---
title: Fehler bei leerem Seiten- oder Umleitungs-Loop beim Zugriff auf Storefront oder Commerce Admin
description: Dieser Artikel bietet eine Lösung für das Problem, wenn Sie auf Adobe Commerce Storefront oder Backend zugreifen und eine leere Seite oder Umleitungsschleife erhalten.
exl-id: 65869de2-1939-481b-844b-69122345b407
feature: Admin Workspace, Cache, Storefront
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Fehler bei leerem Seiten- oder Umleitungs-Loop beim Zugriff auf Storefront oder Commerce Admin

Dieser Artikel bietet eine Lösung für das Problem, wenn Sie auf Adobe Commerce Storefront oder Backend zugreifen und eine leere Seite oder Umleitungsschleife erhalten.

## Betroffene Produkte und Versionen

* Adobe Commerce in der Cloud-Infrastruktur, alle Versionen
* Adobe Commerce vor Ort, alle Versionen
* Magento Open Source, alle Versionen

## Problem

<u>Zu reproduzierende Schritte</u>

Öffnen Sie eine Storefront oder Admin-Seite.

<u>Erwartetes Ergebnis</u>

Die Seite wird geöffnet.

<u>Tatsächliches Ergebnis</u>

Die Seite ist leer oder zeigt die Fehlermeldung &quot;*&quot;Diese Webseite hat eine Umleitungsschleife&quot;* an.

## Ursache

Einer der wahrscheinlichsten Gründe für das Problem ist, dass Adobe Commerce von einer unsicheren URL zu einer sicheren URL umgeleitet wird, aber eine unsichere URL als Wert für die sichere URL-Einstellung angegeben wird.

Um das Problem zu beheben, müssen Sie den Wert des sicheren Links korrigieren.

## Lösung

Gehen Sie wie folgt vor, um sicherzustellen, dass dies die Ursache des Problems ist:

1. Überprüfen Sie den Wert `web/secure/enable_upgrade_insecure` , `web/secure/use_in_adminhtml` (wenn Sie das Leer-/Schleifenumleitungsproblem in Admin haben) oder `web/secure/use_in_frontend` (wenn Sie das Leer-/Schleifenumleitungsproblem auf der Storefront haben) in der DB-Tabelle `'core_config_data'`.
   * Wenn `web/secure/enable_upgrade_insecure` auf &quot;1&quot;gesetzt ist, ist Adobe Commerce so eingerichtet, dass der Antwortheader `Content-Security-Policy: upgrade-insecure-requests` hinzugefügt wird, sodass Browser angewiesen werden, HTTPS zu verwenden, und alle Abfragen umgeleitet werden, die über HTTP kommen
auf HTTPS, sowohl für Admin als auch für Storefront.
   * Wenn `web/secure/use_in_adminhtml` auf &quot;1&quot;festgelegt ist, gibt Adobe Commerce HTTPS-Umleitungen für alle HTTP-Anforderungen für die Admin-Seiten zurück.
   * Wenn `web/secure/use_in_frontend` auf &quot;1&quot;festgelegt ist, gibt Adobe Commerce HTTPS-Umleitungen für alle HTTP-Anforderungen für die Store-Titelseiten zurück.
1. Überprüfen Sie die Werte `web/secure/base_url` und `web/unsecure/base_url` in der Tabelle `'core_config_data'`. Wenn beide mit    `http`, müssen Sie den Wert &quot;sicher&quot;korrigieren.

Behebung des Problems:

1. Legen Sie den Wert für `web/secure/base_url.` auf &quot;`https`&quot;fest.
1. Um die Änderungen anzuwenden, leeren Sie den Konfigurationscache, indem Sie den folgenden Befehl ausführen:

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```

## Verwandtes Lesen

[Best Practices für die Änderung von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Playbook für die Commerce-Implementierung
